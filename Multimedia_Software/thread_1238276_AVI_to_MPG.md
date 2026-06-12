---
title: "AVI to MPG?"
date: 2009-08-12
forum: Multimedia Software
---

### Post by Robbyx on 2009-08-12
What is the best way to convert an AVI file to mpeg -2 for burning to a cd/dvd?

---

### Post by Robbyx on 2009-08-13
Please can I have some help on this. VLC does convert to mpg but so far my cd player does not read its output.

Is there a program that is dedicated to file conversion?

---

### Post by Chronon on 2009-08-13
WinFF is a good front end to ffmpeg.

---

### Post by Robbyx on 2009-08-13
> **Chronon said:**
> WinFF is a good front end to ffmpeg.

Thank you. I have just tried it. The resulting DVD had a picture without subtitles or sound.  Should I have used the additional sound options? If so which ones?

Robin

---

### Post by Robbyx on 2009-08-15
Could I please have some guidance as to why there is no sound or subtitles in the burned mpg?

---

### Post by khelben1979 on 2009-08-15
> **Robbyx said:**
> Could I please have some guidance as to why there is no sound or subtitles in the burned mpg?

Well, I can't help you on that one, however, you might consider testing more applications which is based off ffmpeg. I made a search on sourceforge.net and [here's the result]("http://sourceforge.net/search/?type_of_search=soft&words=ffmpeg").

Maybe you can find something else in there which works better?

---

### Post by cotcot on 2009-08-15
Try [[COLOR="Red"]devede[/COLOR]]("http://www.rastersoft.com/programas/devede.html"). [[COLOR="Red"]Here[/COLOR]]("http://blogcritics.org/scitech/article/making-dvds-with-devede-in-linux/") is a tutorial to make a DVD.

---

### Post by Robbyx on 2009-08-15
> **cotcot said:**
> Try [[COLOR="Red"]devede[/COLOR]]("http://www.rastersoft.com/programas/devede.html"). [[COLOR="Red"]Here[/COLOR]]("http://blogcritics.org/scitech/article/making-dvds-with-devede-in-linux/") is a tutorial to make a DVD.

Did you have a problem with the dependancy not satisfiable: libgtk2.0-0 error message?

---

### Post by Robbyx on 2009-08-15
> **khelben1979 said:**
> Well, I can't help you on that one, however, you might consider testing more applications which is based off ffmpeg. I made a search on sourceforge.net and [here's the result]("http://sourceforge.net/search/?type_of_search=soft&words=ffmpeg").

Maybe you can find something else in there which works better?

Thank you that was very considerate.

I have tried a few but although I am using intrepid there was dependancy problems. Can you suggest one that has a gui and will work. DeVeDe look very good but it has a dependancy missing problem.

---

### Post by cotcot on 2009-08-16
> **Robbyx said:**
> Thank you that was very considerate.

I have tried a few but although I am using intrepid there was dependancy problems. Can you suggest one that has a gui and will work. DeVeDe look very good but it has a dependancy missing problem.

I have used devede in intrepid without problems. 
It might be useful to explain which dependency problems your encounter. You can get dependency problems if try to install too recent version of devede. Check [[COLOR="Red"]this[/COLOR]]("https://launchpad.net/ubuntu/+source/devede").

---

### Post by Robbyx on 2009-08-16
> **cotcot said:**
> I have used devede in intrepid without problems. 
It might be useful to explain which dependency problems your encounter. You can get dependency problems if try to install too recent version of devede. Check [[COLOR="Red"]this[/COLOR]]("https://launchpad.net/ubuntu/+source/devede").

Thank you. I went to Synaptic and installed it from there. It loaded well but when I ran a file conversion there was an error report that there may be a bug in mencode. I had previously been  reported as a bug but I could not see any correction advice. 

Do you have a solution?

---

### Post by Robbyx on 2009-08-16
> **Robbyx said:**
> Thank you. I went to Synaptic and installed it from there. It loaded well but when I ran a file conversion there was an error report that there may be a bug in mencode. I had previously been  reported as a bug but I could not see any correction advice. 

Do you have a solution?

I have just changed the location of the output file and it is no longer giving the error message.

---

### Post by cotcot on 2009-08-17
I have mencoder and ffmpeg compiled from source through SVN (not because of dvd but because of support for AVCHD video).
I had no dependency problems with devede.

I jaunty I upgraded devede because I wanted to use a feature in imagemagick 6.5 and this required devede 3.14. So I had to compile both.

---

