---
title: "Acrobat for Linux?"
date: 2017-12-20
forum: Multimedia Software
---

### Post by primuspaul on 2017-12-20
Is there anything that comes close to being like Acrobat for Linux? I get so much work done very quickly using Acrobat on a Win7 PC. Arranging pages, combining files, inserting and extracting pages, typing over the document, are all so easy and fast. With Ubuntu, just VIEWING the PDF files (even ones with just a few pages) is a pain. I tried different viewers and they both take eternity to generate the pages, which appear white until loaded, and crash unpredictably.

---

### Post by ian-weisser on 2017-12-20
[s]PDF is a proprietary format owned by Adobe.
Consider asking them for a stable Linux PDF management application.

Open source developers would *love* to create an Acrobat-like application, but Adobe tends to sue folks that try.[/s]

Thanks to Nader_Nooryani in Post #7 for the correction.

---

### Post by primuspaul on 2017-12-20
> **ian-weisser said:**
> PDF is a proprietary format owned by Adobe.
Consider asking them for a stable Linux PDF management application.

Open source developers would *love* to create an Acrobat-like application, but Adobe tends to sue folks that try.
What's an alternative to PDF that is open source and works with Linux?

---

### Post by ajgreeny on 2017-12-20
Are you trying to create PDFs or edit them?

If the latter, have a look at **master-pdf-editor** which is available as a free for personal use application.
I have never used it personally but many other users have and suggest it is the best application available for linux.

See [https://askubuntu.com/questions/942373/what-software-can-i-use-to-write-on-pdfs](https://askubuntu.com/questions/942373/what-software-can-i-use-to-write-on-pdfs) for much more info.
You can download it from [https://code-industry.net/free-pdf-editor/#get](https://code-industry.net/free-pdf-editor/#get)

---

### Post by monkeybrain20122 on 2017-12-20
> [COLOR=#000000]Arranging pages, combining files, inserting and extracting page[/COLOR]

Install pdfchain, it is in the repo.

Also if you paid for Acrobat professional you can check out PDF studio, it works on Linux, but it costs you $$$ but cheaper than Adobe.

---

### Post by sccman on 2017-12-20
You could install the Windows version of Acrobat on Linux using Wine.

Wine install instructions for Ubuntu: [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

Then run:

```
wine /path/to/Acrobat-installer.exe
```

---

### Post by Nader_Nooryani on 2017-12-20
I thought so as well until a friend corrected me.

> Adobe Systems made the PDF specification available free of charge in 1993. PDF was a [proprietary format]("https://en.wikipedia.org/wiki/Proprietary_format") controlled by Adobe, until it was officially released as an [open standard]("https://en.wikipedia.org/wiki/Open_standard") on July 1, 2008, and published by the [International Organization for Standardization]("https://en.wikipedia.org/wiki/International_Organization_for_Standardization") as ISO 32000-1:2008 Ref. [https://en.wikipedia.org/wiki/Portable_Document_Format#History_and_standardization](https://en.wikipedia.org/wiki/Portable_Document_Format#History_and_standardization)

I think the main issue is that it is not meant necessarily designed to be edited, rather to be used as an output format created from something like a Word document etc.   Correct me if I am wrong.   I have been looking for this myself and I think the best option would be to use something like Nuance Power PDF with Wine or Master PDF Editor.   Both of these are proprietary, but I believe you need to use the best tools available if you need them.

---

### Post by zerubbabel on 2018-03-06
Master PDF Editor is good, but [PDF XChange Editor]("https://www.tracker-software.com/product/pdf-xchange-editor") is better, reasonably priced, and runs fine under Wine.

---

