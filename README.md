# Veracity for Developers Documentation
Welcome to the open source documentation for [Veracity for Developers](https://developer.veracity.com/docs). Here you will find all the source files for the documentation on Veracity for Developers.

## File structure
The documentation is organized into sections where each section can define not only which document should be contained within it, but also where it can be found. The root of the repository defines a set of known folders in which documentation can be placed:

Folder|Description
-|-
`common`|A folder containing legacy documentation. Future documentation should be placed in the `sections` folder under a relevat section.
`schemas`|A folder containing JSON schemas defining known json object such as the table of contents (`toc`).
`sections`|The root folder for documentation sections. This is where you should place all documentation.

## Sections
Documentation is structured in separate folders under the `sections` root folder. Each section should comprise documentation for one service or product. Sections are parsed automatically and deployed to the documentation website upon approval from an owner of the repository.

A section consists of a set of markdown files containing the actual documentation. All common markdown elements are supported in addition to plain HTML tags. Below is a set of best practices you should follow when writing documentation:

- Section folder names must be camel-cased and cannot contain spaces or other characters that are illegal in urls. Recommended set of characters is: `a-z A-Z 0-9 - _`

- Each section folder `MUST` have a table of contents file at its root named `toc.json`. This file must match the schema defined in `schemas/toc.json`. To create a new table of contents create an empty json file at the root of a section named `toc.json` and add this content to get started:
```json
{
	"$schema": "../../schemas/toc.json",
	"items": []
}
```

- Markdown files are written as normal markdown with a "front matter" section containing metadata. Front matter is written at the top of the markdown file like this:
```markdown
---
author: Jane Doe
description: Some information about the document that is displayed in the description meta tag
---
```

- Any asset files such as images and videos must be placed in a folder called `assets`. Any sub-folder within a section can contain an `assets` folder. Linking to assets from markdown files is done using relative links from the markdown file itself. This ensures the files can be viewed correctly on GitHub as well as on the documentation page. Assets are uploaded to the CDN automatically upon approval.

- Image links should be wrapped in `<figure>` html tags, and must include the `alt` attribute. Example:
```html
<figure>
	<img alt="Protocol diagram showing communication between application, server and the Veracity IDP" src="assets/basic-oidc-authentication.png"/>
	<figcaption>An application with direct user interaction can redirect the user to the login page to authenticate them.</figcaption>
</figure>
```
