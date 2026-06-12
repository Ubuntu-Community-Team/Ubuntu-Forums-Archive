---
title: "PDF viewer for viewing Embedded movies in presentation."
date: 2012-03-17
forum: Multimedia Software
---

### Post by souravc83 on 2012-03-17
After shifting to Ubuntu, I have started making my presentations using the latex beamer package. A totally great package to use, despite the relatively steep learning curve.

However, the only problem I am facing is to display embedded movies in my presentation.I can create the content just fine, but the problem is that I cannot **play it on any pdf viewer in Ubuntu**.


 I am trying to play the movie in the pdf which can be downloaded from [[COLOR="Red"]here[/COLOR]]("http://pages.uoregon.edu/noeckel/computernotes/movieExample/movie.pdf").


1)Adobe Reader does not play embedded movies, because it requires realplayer to play them.
2) I have tried evince. Evince opens a separate window to play the movies in the normal mode (this is okay, acceptable to me), but in the presentation mode, this does not work. I searched the web a bit, and found that this was a bug in evince which has been corrected in the latest version. I am using the latest stable version, which is 3.2, but this still happens in my system. So Evince does not work either.
3) I have tried okular. But it just brings up an yellow textbox when I click on the movie.

Does anyone have a solution, which will allow me to play an embedded movie in a presentation in a pdf viewer?

I am not too concerned about the format. I can embed whichever format works.

(The only other thing that apparently used to work is Acrobat Reader 7. This is what this [[COLOR="red"]old post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=592859") in the ubuntuforum says. However, I could not find the Acrobat 7 installation files for linux on the web, so could not test this solution too)vvv

---

### Post by Rodney9 on 2012-03-17
This may help -

[http://vimalkumar.in/2010/05/23/embed-movies-in-pdf-documents-with-lyx-latex-beamer-and-movie15/](http://vimalkumar.in/2010/05/23/embed-movies-in-pdf-documents-with-lyx-latex-beamer-and-movie15/)

Rodney

---

### Post by souravc83 on 2012-03-18
Thanks Rodney. 
What I am stuck at is the ability to play the video in any pdf reader in Ubuntu.
The blog also mentions you cannot test it (i.e play the video in the pdf file) on linux.
I am curious if there is a workaround that allows you to play the video in Ubuntu, using either Acrobat, evince or okular (ar any other pdf reader).

---

### Post by Chronon on 2012-03-18
I haven't tried this yet but it appears promising.
[http://pages.uoregon.edu/noeckel/PDFmovie.html](http://pages.uoregon.edu/noeckel/PDFmovie.html)

---

### Post by souravc83 on 2012-03-18
Hi Chronon,
I went through that.
This is fine.

But my problem is not with creating the multimedia content, it is with playing it in any pdf reader in Ubuntu.

The above author uses a mac system for his content. 

Maybe I should have posed the initial question more clearly. I can create the pdf content just fine, but I am having problems playing the content on an Ubuntu system.

---

### Post by ImRe0 on 2012-06-25
Hello!

I wonder if you have found some solutions for this, because I came across this problem as well... I am trying to use the 'media9' package for embedding video files, but I cannot really play them neither under Evince, nor Okular, nor Adobe Reader. (Foxit doesn't even start for me...) Furthermore, it seems, that from the 9.4.1 release for Linux, Adobe disabled the support for playing flash videos. 
So I am curious, if since your post, did you find any solution? Some workaround method, other PDF viewer?

(PS.: The videos work fine under Window 7, Adobe Reader 9.5.1)

---

### Post by sevonne on 2012-08-30
Hello!
I managed to read a video embedded within a pdf file with okular.
The pdf was created with latex beamer and the video was .flv format.
I do not know if other format will be readable as well.

The only default is that the still picture that was in my presentation (i.e. the picture you click on to start the video) shows up as a black rectangle. This is a minor problem, because what I really want is the video.

---

