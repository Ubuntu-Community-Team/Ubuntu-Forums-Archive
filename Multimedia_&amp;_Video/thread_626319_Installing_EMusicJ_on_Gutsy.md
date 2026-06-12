---
title: "Installing EMusicJ on Gutsy"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by NET WT on 2007-11-28
Hi, I just downloaded  [EMusicJ]("http://www.kallisti.net.nz/EMusicJ/HomePage"), but I don't know how to install it. Can someone help me with that? Also, has anyone here installed it on 7.10? Because I am wondering if it is going to work on my computer. Thanks for any help.

---

### Post by sojyujai on 2007-12-04
Hey, I had a similar question and found your thread while looking for an answer.  It turns out that installing it is fairly simple and I pretty much figured it out on my own. For me it just worked with gutsy (amd64) - although I am using sun java 6 instead of the icedtea java that came with my version of gutsy.  Not sure if that makes any difference to running emusicj but it did make a big difference for running azureus which is why I switched.

This is what I did:
First download the correct version of emusicj from here (a .tar.gz file) [http://www.kallisti.net.nz/EMusicJ/Download]("http://www.kallisti.net.nz/EMusicJ/Download")
- double-click it and extract it into your home directory
- navigate into the extracted emusicj-linux directory
- double-click the emusicj file and in the dialogue that opens hit 'Run'

If it works emusicj should open and start running.  That's all you really need to do.  You could leave the emusicj-linux directory in your home directory and run it from there.  Or, what I prefer to do is move it into the /opt directory.
- In a terminal enter: gksudo nautilus /opt
- give it your password
- /opt should open in nautilus with root privileges - just drag the emusic-linux directory into it, then close the window.

Now setup an entry in the main menu
- System > Preferences > Main Menu
- highlight 'Sound & Video' then click 'New Item'
- for Name enter 'EmusicJ'
- for Command enter '/opt/emusicj-linux/emusicj'
- click the springy icon thing in the top left
- in the location bar in the window that opens enter '/opt/emusicj-linux/emusicj.xpm'

Now you should have a menu item with a nice icon that will launch emusicj

Last thing is to associate the emusic .emp files with emusicj in firefox.  
- On the emusic website click a download link for music (single song or whole album) 
- the dialogue window that opens will ask you: 'Open With..' or 'Save'.  Select 'Open With' and browse to /opt/emusicj-linux/emusicj 
- click the check-box 'automatically do this for files of this type' 

Now you should be all set.

---

### Post by happyisland on 2007-12-08
Thanks for the user-friendly how-to, sojyujai! They should post your entry on the emusicj site - very handy.

---

### Post by eythian on 2008-01-15
> **happyisland said:**
> Thanks for the user-friendly how-to, sojyujai! They should post your entry on the emusicj site - very handy.
They (well, I) did :)

[http://www.kallisti.net.nz/EMusicJ/Installation]("http://www.kallisti.net.nz/EMusicJ/Installation")

Sometime soon I need to update that page and make it a bit more step-by-step. Oh, and I develop it in Ubuntu 7.10, both 32 and 64-bit. It'll be the best supported platform for eMusic/J out there.

---

### Post by NET WT on 2008-01-22
Thanks for the how-to. I have been using v0.22 and it works good. I noticed that there is a newer version available though, and would like to upgrade. I am not sure how to do that.

---

### Post by sojyujai on 2008-01-23
Glad the howto is proving useful.

I haven't done the upgrade so I can't tell you exactly what to do but I'll give you my idea about what I think will work.  I would think the best thing would be to remove the old version then install the new version.  EmusicJ runs completely out of the emusicj-linux directory.  You should be able to remove it by just deleting that directory.  If you put it in /opt then you'll need root privelidges to remove it so use gksudo as described above or sudo within the terminal.

Once the old version is gone you should be able to install the new version as described in my above post.  I'd hope the new version uses the same filenames for the start-up script and the icon - if so the main menu entry you already made should still work.  If not you'll need to check the readme file or the installation instructions on the emusicj website to see which file you need to execute to run it, then modify the main menu entry to point to that file.  You would also need to change the firefox settings to open .emp files with that same file.

---

### Post by eythian on 2008-03-23
> **sojyujai said:**
> I haven't done the upgrade so I can't tell you exactly what to do but I'll give you my idea about what I think will work.  I would think the best thing would be to remove the old version then install the new version.  EmusicJ runs completely out of the emusicj-linux directory.  You should be able to remove it by just deleting that directory.This is a bit of a late response, I forgot to subscribe to the thread. Anyway, in case it's useful for others, your response is exactly correct, although it is simpler than that: you can just extract the new version over the top of the old one. All the files will be replaced with new versions, and it'll be happy.

There is one old release where that's not recommended, as I changed the file layout, but that's noted on the download page.

---

