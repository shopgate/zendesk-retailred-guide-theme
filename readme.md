# Shopgate Zendesk Style

this project is used to give our zendesk guide (retail.red) a customized style.

## How to use

first, install the dependencies via

```shell
npm install
```
or

```shell
yarn install
```

then edit the `src/style.scss` file according to the needs.

At the end run

```shell
npm run compile
```
or

```shell
yarn compile
```

and copy the contents of `dist/style.css` to the `article_page.hbs` as
documented here.

### Where to put the styles?
This customization is targeted at the article's page (`article_page.hbs`). There for you must open the article's page code\
in zendesk admin panel, and inject the content of the `dist/style.css` to the top of the template.

then inside of the template, in the place where we need to show the menu, put the following line:

```html
<ul id="toc" class="table-of-contents"></ul>
```

at the end of the template file, add these configurations:

```html
<script type="text/javascript">
    $("#toc").toc({content: ".article-body", headings: "h2,h3,h4"});
</script>

<script type="text/javascript">
  $('.table-of-contents').stickySidebar({
    topSpacing: 60,
    bottomSpacing: 60
  });
</script>
```

**⚡️ Danger!** Do not forget to add these three javascript dependencies in the same order on top of the template file `article_page.hbs`:

```html
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://rawcdn.githack.com/ndabas/toc/d84b1dd1172be7a6337fe1ab16726636c1896d9d/jquery.toc.js"></script>
<script src="https://rawcdn.githack.com/abouolia/sticky-sidebar/bcd40bbf95e84b75916bc3535d7475447f9383f8/dist/jquery.sticky-sidebar.min.js"></script>
```

#### Example
```html
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://rawcdn.githack.com/ndabas/toc/d84b1dd1172be7a6337fe1ab16726636c1896d9d/jquery.toc.js"></script>
<script src="https://rawcdn.githack.com/abouolia/sticky-sidebar/bcd40bbf95e84b75916bc3535d7475447f9383f8/dist/jquery.sticky-sidebar.min.js"></script>

<style>
	/* styles from `style.css` will be here */
</style>

<!-- The rest of the template -->

<div class="container-divider"></div>
<div class="container">
	<!-- ... -->
  <div class="article-container" id="article-container">
    <aside class="article-sidebar" aria-labelledby="section-articles-title">
      <ul id="toc" class="table-of-contents"></ul>
	  <!-- ... -->
    </aside>

	<!-- ... -->

  </div>
</div>

<script type="text/javascript">
    $("#toc").toc({content: ".article-body", headings: "h2,h3,h4"});
</script>

<script type="text/javascript">
  $('.table-of-contents').stickySidebar({
    topSpacing: 60,
    bottomSpacing: 60
  });
</script>
```