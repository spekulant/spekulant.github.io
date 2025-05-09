## Hello there!

You found the source code of my personal site and blog. It's a hand crafted static site without any CMS, just plain HTML and CSS.

## Adding new articles

Given a markdown article file named:

`post-16-05-24-install-dmg-with-nix-darwin.md` in `_mdposts` directory.

You can convert it to html with the [`markdown` python package](https://www.linode.com/docs/guides/how-to-use-python-markdown-to-convert-markdown-to-html/) like below:

```bash
python3 -m markdown _mdposts/post-16-05-24-install-dmg-with-nix-darwin.md > post.html
```

Then, use the template page to give the post a proper layout:

```bash
sed '/<!--- content --->/ {
r post.html
d
}' templates/page.html > output.html
```

Be sure to inspect the resulting html file as the py package's expected md formatting is slightly different than the Github's markdown variant. (So, eg. code blocks are not marked with backticks but with four spaces)

If there are any footnotes you want to refer to, wrap the section in a href and add the following id to the footnotes paragraph.

```md
[[P1](#footnotes)]
```

```html
<h3 id="footnotes">Przypisy</h3>
```

Finally, move the output to the posts directory, remove the temporary files and link the new post in the `blog/index.html` file.

```bash
mv output.html blog/post-16-05-24-install-dmg-with-nix-darwin.html
zed blog.html
rm output.html
rm post.html
```

## Color palette

- ethereal ivory #E4E4DE
- sophisticated sage #C4C5BA
- timeless noir #1B1B1B
- muted moss #595f39

## License

Licensed under [Creative Commons Attribution 4.0 International license](https://creativecommons.org/licenses/by/4.0/) unless otherwise noted.
