---
title: "Flac to MP3 Converter"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by Shiner_Man on 2007-04-18
What is the easiest application to convert flac files to mp3 or ogg?

---

### Post by mojoman on 2007-04-18
If you're using Gnome I'd suggest soundconverter. Really easy to use and quite efficient. Now, I'm using xfce as a desktop and soundconverter downloads tons of Gnome dependencies that I don't want to bloat my system with, otherwise I'd still be using it. Instead, I'm desperately searching for an alternative to soundconverter...

/mojoman

---

### Post by Shiner_Man on 2007-04-18
That's exactly what I was looking for.  Thank you.

---

### Post by yabbadabbadont on 2007-04-18
> **mojoman said:**
> If you're using Gnome I'd suggest soundconverter. Really easy to use and quite efficient. Now, I'm using xfce as a desktop and soundconverter downloads tons of Gnome dependencies that I don't want to bloat my system with, otherwise I'd still be using it. Instead, I'm desperately searching for an alternative to soundconverter...

/mojoman

Bash shell script: [http://www.bytemonkey.org/projects/flac2mp3/](http://www.bytemonkey.org/projects/flac2mp3/)

Perl script: [http://freshmeat.net/projects/flac2mp3/](http://freshmeat.net/projects/flac2mp3/)

I've used the bytemonkey script with success in the past.

---

### Post by mojoman on 2007-04-19
> **yabbadabbadont said:**
> Bash shell script: [http://www.bytemonkey.org/projects/flac2mp3/](http://www.bytemonkey.org/projects/flac2mp3/)

Perl script: [http://freshmeat.net/projects/flac2mp3/](http://freshmeat.net/projects/flac2mp3/)

I've used the bytemonkey script with success in the past.

Yeah, script seems to be a good way to do it but a lot of scripts are limited in the number of formats they handle as well as the direction of conversion. I've also been looking into sox, which is able to convert to and from most formats. However, I would really like an easy, lightweight gui converter that is able to convert to and from as many formats as possible. Anyway, thanks for the tips, I appreciate it.

/mojoman

---

### Post by mal on 2007-04-27
> **yabbadabbadont said:**
> Bash shell script: [http://www.bytemonkey.org/projects/flac2mp3/](http://www.bytemonkey.org/projects/flac2mp3/)

Perl script: [http://freshmeat.net/projects/flac2mp3/](http://freshmeat.net/projects/flac2mp3/)

I've used the bytemonkey script with success in the past.

Note that, to get the perl script working in Feisty, I had to change the first line of flac2mp3.pl from ```
#!/bin/env perl 
```to ```
#!/usr/bin/env perl
```

Also make sure to: ```
$sudo apt-get install flac lame
```

Mal

---

