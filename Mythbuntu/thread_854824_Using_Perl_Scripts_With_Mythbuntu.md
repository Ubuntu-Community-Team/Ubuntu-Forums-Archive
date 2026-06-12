---
title: "Using Perl Scripts With Mythbuntu"
date: 2008-07-09
forum: Mythbuntu
---

### Post by mharter on 2008-07-09
Hello, I would like to run this perl script to get video thumbnails for files without movie posters:

[http://www.mythtv.org/wiki/index.php/Generatevideothumbs.pl](http://www.mythtv.org/wiki/index.php/Generatevideothumbs.pl)

However, I have no idea how to use perl scripts.  Can someone help me by writing some detailed instructions to run these types of scripts?  Will this script even work?

Thanks for your help!

---

### Post by freymann on 2008-07-09
> **mharter said:**
> Hello, I would like to run this perl script to get video thumbnails for files without movie posters:

[http://www.mythtv.org/wiki/index.php/Generatevideothumbs.pl](http://www.mythtv.org/wiki/index.php/Generatevideothumbs.pl)

However, I have no idea how to use perl scripts.  Can someone help me by writing some detailed instructions to run these types of scripts?  Will this script even work?


 Hmmm.

 Well, basically, you'd select the script and copy it.

 Then you'd have to save the contents into a file on your computer and paste the contents into the file.

 You could block the script, edit > copy....

 Open up a terminal...

 Decide where to put the script, say

 cd /usr/sbin

 sudo pico generatevideothumbs.pl

 Then paste the contents into the editor.

 Then exit and save the file.

 Now you have to make the script "executeable" by:

 sudo chmod 775 generatevideothumbs.pl

 And to "run it" at the shell you could:

 sudo ./generatevideothumbs.pl

 That would likely run it, but what it does I don't know.

 My info also assumes you know how to open up a terminal session, and hopefully the editor "pico" is installed. nano is another.

 sudo apt-get install nano

 if you need.

---

### Post by mharter on 2008-07-10
Thank you for your help.  I am familiar with using the terminal and nano but I just didn't know how to use scripts.  I will try this when I get a chance and post an update.

---

