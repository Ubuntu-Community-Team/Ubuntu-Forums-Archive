---
title: "Password protected pdf no longer open"
date: 2018-07-26
forum: Multimedia Software
---

### Post by kazakore on 2018-07-26
My work provides my payslips in a password protected pdf file. I check this every month I receive it. Today I have just got a new one and for the first time I can not view it, I am never given a prompt to enter the password as I usually would be, and it opens with errors (obviously) although it should refuse to open and say incorrect password.

Usually I open with what is just called Document Viewer. Sorry I don't know what program this actually is.

Also tried in E-book Viewer, which I believe is installed alongside Calibre but unsure if part of it or just a dependency. This gives:
> calibre, version 3.21.0
ERROR: Could not open e-book: Failed to read book, /tmp/mozilla_dale0/Payslip (2018-06-27 Period 3).pdf click "Show Details" for more information

Traceback (most recent call last):
  File "/usr/lib/calibre/calibre/utils/ipc/simple_worker.py", line 284, in main
    res = {'result':func(*args, **kwargs)}
  File "/usr/lib/calibre/calibre/ebooks/oeb/iterator/book.py", line 65, in extract_book
    plumber.opts, plumber.input_fmt, log, {}, tdir)
  File "/usr/lib/calibre/calibre/customize/conversion.py", line 245, in __call__
    log, accelerators)
  File "/usr/lib/calibre/calibre/ebooks/conversion/plugins/pdf_input.py", line 51, in convert
    pdftohtml(os.getcwdu(), stream.name, options.no_images)
  File "/usr/lib/calibre/calibre/ebooks/pdf/pdftohtml.py", line 92, in pdftohtml
    raise ConversionError(b'pdftohtml failed with return code: %d\n%s' % (ret, out))
ConversionError: pdftohtml failed with return code: 1
Command Line Error: Incorrect password
But never asks for the password to be entered in the first place. So how can it be incorrect?!?!


What has broken since I received my payslip last month and why?


EDIT:
Oops thought I was in General. Would somebody mind moving this for me?

---

### Post by kazakore on 2018-07-26
Document Viewer is "Evince"

```
sudo apt remove --purge evince* # there's also an evince-common which didn't get removed otherwise
sudo apt autoclean
sudo apt install evince

```

and it's back as it should be.

---

