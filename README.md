
---
title: Latex template for CLAS-compatible CVs
author: Cesare Tinelli
date: Nov 2020
updated: April 2021
---

This repository contains a Latex CV Template compatible with Word template recommended by the College of Liberal Arts and Science of the University of Iowa.

### Included files

* `README.mb`, this file.

* `cv-template.tex` contains a latex template for a CV largely conforming to the CLAS standard CV.
Identifiers in `cv-template.tex` starting with @ are informal meta variables to be replaced manually with the actual data.

* File `cv-template.pdf` is the compiled version of `cv-template.tex` produced by pdflatex.
Generate it as usual but _use biber instead of bibtex._

* `macros.tex` is imported by `cv-template.tex` and contains the macros used in `cv-template.tex`, as well as all the relevant package imports.

* `sample.bib` contains a sample bibtex file, the source of the bibtex entries used by biber.
It is imported by `cv-template.tex` with the command
`\addbibresource{sample.bib}`.

* `clas-standard-cv-template.docx` is the Word template provided by CLAS

### Publications subsection

The entries for the publication subsection are generated _automatically_ using the **[biblatex](https://ctan.org/topic/biblatex)** package and **[biber](https://ctan.org/pkg/biber)** (a more modern version of bibtex).
Recent [TeXLive](https://www.tug.org/texlive/) distributions include by default biblatex, biber, and every package imported in `cv-template.tex`.

The options of biblatex explicitly set in `macros.tex` are:
* `backend=biber` This is actually the default. The value can be changed to `bibtex` but with limited functionality. Not recommended.
* `style=ieee` Among the bibliography formats supported by biblatex, this is the closest to the format of the CLAS standard, with the only relevant exception that author names are listed with first name initial and last name (instead of last name and first name initial). This will have to do because the other pdflatex formats deviate even more.  

* `sorting=ydnt` causes entries to be sorted by year (in descending order), name, and title
* `defernumbers=true` allows local numbering of bibliography per subsection.

### Bibtex entries

The entries in `sample.bib` are standard bibtex entries but with these additional attribute-values pairs used by biblatex to select desired entries:

* `keywords` contains a keyword used by biblatex as a filter. Currently, possible values are 
   - `nonref` for non-refereed articles publications, 
   - `electronic` for books or proceedings that are published only in electronic form,
   - `review` for reviews,
   - `abstract` for non-refereed abstracts.

* `options` is used to provide, as a biblatex option, the level of contribution of each publication (expressed as a string of asterisks) as required by CLAS. The value has to have the form `contrib=*`, `contrib=**`, and so on. 
The macros `\majorc`, `\equalc` can be used in alternative to the asterisks.

Note that the `doi` and `url` attributes are directly supported by biblatex and are automatically converted into the proper URL link in the PDF.

Look for the command `\printbibliography` in `cv-template.tex` to see how each publication subsection is generated.
The option `resetnumbers=true` in there generates a local numbering of the entries per section. This numbering might get messed up when new entries are added to the `.bib` file(s). In that case, as with bibtex, deleted all the auxiliary files generated by pdflatex and biber and rerun them.

The other options of `\printbibliography` are filtering options.
