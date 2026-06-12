---
title: "Multi page document file"
date: 2019-11-21
forum: Multimedia Software
---

### Post by bill-lancaster on 2019-11-21
Scanimage works well but when trying to scan multiple pages I have a problem.
```
scanimage --mode Gray --resolution 300 --format=tiff --batch=document-p%d.tiff --batch-prompt
```
Scans the first page then fails with the second, this is the output
Place document no. 1 on the scanner.
Press <RETURN> to continue.
Press Ctrl + D to terminate.

Scanning page 1
Scanned page 1. (scanner status = 5)
Place document no. 2 on the scanner.
Press <RETURN> to continue.
Press Ctrl + D to terminate.

Scanning page 2
scanimage: sane_start: Invalid argument
Batch terminated, 1 page scanned

Any help welcomed
Kubuntu 18.04
P.S. This was posted yesterday in the wrong section (hardware)

---

### Post by TheFu on 2019-11-22
I've been using **gscan2pdf** for years - perhaps a decade now. I have an autofeeding scanner, so all the pages in a single feed are put into the same PDF file.  It also has OCR which isn't great, but gets placed _under_ the scanned images for the page so text and pdf searching will find the pages, within the limits of the OCR.

I don't use kubuntu or 18.04, so don't know how well it will or won't work on that setup.

---

### Post by bill-lancaster on 2019-11-23
Thank you for that, it works fine on 18.04 and it's still in the repository.
Problem solved

---

