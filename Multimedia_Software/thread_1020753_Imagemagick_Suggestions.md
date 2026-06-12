---
title: "Imagemagick Suggestions"
date: 2008-12-24
forum: Multimedia Software
---

### Post by crazyness003 on 2008-12-24
Hello.

Im trying to convert a bunch of PDF's into something else that readable across many platforms.
My goal is this:
Take PDF's ranging from 35-200KB and convert them into another file format (or even maintain pdf) while reducing the filesize to about 5-10KB and still maintaining a readable record that can be printed onto 8.5x11 (216x279mm) paper without loss of readability. I could care less for graphics.

I tried using the[FONT=Fixedsys] [FONT=Courier New]-monochrome[/FONT][/FONT] option, but that just makes the text look horrible
Also i tested out diff file formats and so far out of TIFF, JPEG and GIF; The lowest filesize i got was with GIF. Is there anything smaller

So i ask:

[LIST]
[*]What file format is platform-independant, small, and printable?
[*]What options should i throw at imagemagick to make files smaller while still maintaining readable charachters and printable document sizes without ugly stretching?
[*]How can I use files with spaces in them in the terminal. ie: "record onsite 20081224.pdf" (this one should be easy)
[*]If there is another way to do this quick, fast and in a hurry with another app (doubtful)
[/LIST]

Thanks in advanced. Im gonna keep experimenting, but if anyone can give me a shortcut, id appreciate it

EDIT: Another thing i forgot to ask was: If i can do this with multiple files at once in imagemagick

---

### Post by kaibob on 2008-12-24
Posting deleted by Kaibob

---

### Post by crazyness003 on 2008-12-26
bump

---

### Post by soxs on 2008-12-26
files with spaces (use one option at time):
a) avoid spaces in file names, use underscores instead
b) use " around your filename
c) escape spaces with backsashes right before the spaces. hallo\ omega.avi for example

BTW

200kb is pretty small. You should think about keeping them "as is". PDF are extremy plattform independant, except for jpeg, gif.. etc, but they are not what you want. Either they will suck quality wise or will exceed the input pdf size.
I'd suggest you, get a new hd if you're in need of bytes/space on your hddev.

---

### Post by crazyness003 on 2008-12-26
> **soxs said:**
> files with spaces (use one option at time):
a) avoid spaces in file names, use underscores instead
b) use " around your filename
c) escape spaces with backsashes right before the spaces. hallo\ omega.avi for exampleThanks for the spaces info. you get a [img]http://ubuntuforums.org/images/buttons/post_thanks.gif[/img] :D
> **soxs said:**
> ...200kb is pretty small. You should think about keeping them "as is". ... jpeg, gif...etc... are not what you want. **Either they will suck quality wise** or **will exceed the input pdf size.**As for the converting, im backing up these on a portable flash-drive at the moment. The originals I keep unscathed, but as for my backups, i dont need that much quality, I just want to be able to read the text. I know how quality can be reduced (i tried the [FONT=Courier New]-monochrome[/FONT] option: unacceptable! 
BUT: what do you mean by "will exceed input pdf size"?
Are you talking about actual dimensions (WxH) or filesize (>200KB)?
> **soxs said:**
> I'd suggest you, get a new hd if you're in need of bytes/space on your hddev. I guess i could store them on a bigger flash-drive. They got extremely cheap nowa days. Right now im using 512MB, but I guess im due for an upgrade.

Im now starting to wonder if i should get some sorta OCR app and convert them to .txt. I can reduce a 200KB PDF (with unecessary graphics) to 2KB TXT (I attempted this with a simple ctrl+c of the pdf text, ctrl+v to an empty plain text document. Not to asthetic and the end result is a little garbled up).

Well thanks anyway, im gonna wait and see if i should deviate now. Maybe someone has a different opinion.

---

### Post by soxs on 2008-12-26
I meant filsize.

---

### Post by kaibob on 2008-12-26
> **crazyness003 said:**
> Im now starting to wonder if i should get some sorta OCR app and convert them to .txt. I can reduce a 200KB PDF (with unecessary graphics) to 2KB TXT (I attempted this with a simple ctrl+c of the pdf text, ctrl+v to an empty plain text document. Not to asthetic and the end result is a little garbled up).

Well thanks anyway, im gonna wait and see if i should deviate now. Maybe someone has a different opinion.

There's a pdf to text command-line converter in the repo's. It's a part of the poppler-utils. 

[http://linux.die.net/man/1/pdftotext](http://linux.die.net/man/1/pdftotext)

It doesn't work with all PDF's, but it should work with any PDF that allows you to copy and paste text. With the default settings, the results can be a bit run-on, so you may have to play around with the options (e.g. -layout).

---

