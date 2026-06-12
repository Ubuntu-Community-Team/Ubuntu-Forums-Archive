---
title: "Shoutcast in Streamtuner"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by luvz_mocha on 2008-03-17
**This post could be related to an Ubuntu bug filed at**: [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/efc6cadd7227f1e2](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/efc6cadd7227f1e2) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Shoutcast has stopped listing in Genres. I found the fix today but being a complete newb I need to know where the plugin fix goes. Any help would be greatly appreciated. Running Gutsy.

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/efc6cadd7227f1e2](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/efc6cadd7227f1e2)

---

### Post by richieboy on 2008-03-18
please!!!  someone help us noobs!!!  i know we have to paste the new text in.  but where?

---

### Post by richieboy on 2008-03-18
if you installed streamtuner using aptitude or apt-get, you'll need to remove --purge that installation because you need to edit the shoutcast.c source file.  download the streamtuner source from the site, untar it, go into the src directory and open shoutcast.c in a text editor.  make sure the editor shows line numbers.

the maroon text shows the line numbers and spaces where to add  the new text.  now just add the blue text in the .diff patch file into the shoutcast.c file.  DON'T ADD THE + SIGNS!
you might have to look around and match up the lines in context; my line numbers didn't match the .diff file's line numbers.

save the file.  run ./configure, make, and sudo make install and IT WORKS!!!

OH YEAH!!  the red text with the - signs is text to delete from the shoutcast.c file.

---

### Post by yonkman on 2008-03-25
Thanks for then instructions it worked like a charm.  Just make sure to reinstall xmms afterward (didn't even lose my settings!!)

One thing, I ran into a lot of "can't find" messages when I tried to run the "./configure" command.

  Basically, I had to install the "*-dev" packages for each of these (GCC, GtK+, LIBcurl,  another one I think).  It was a little frustrating as the packages themselves were there, just not the -dev files.

Hope this saves someone else the same headache.

Great fix!

OH, one thing from the preceding message.  "download the streamtuner source from the site" refers to the SteamTuner site not Ubuntu repositories.

---

