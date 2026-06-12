---
title: "vlc wont start"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by jonpon on 2007-11-14
I have installed vlc on feisty but when I go to Applications/sound and video /vlc nothing happens. 
Can anyone tell me how to kick start it!
thanks

---

### Post by rsambuca on 2007-11-14
> **jonpon said:**
> I have installed vlc on feisty but when I go to Applications/sound and video /vlc nothing happens. 
Can anyone tell me how to kick start it!
thanks

Type 'vlc' in a terminal and see if an error message shows.

---

### Post by jonpon on 2007-11-14
I get no error in terminal
just this

jonpon-laptop:~$ vlc
VLC media player 0.8.6 Janus
Remote control interface initialized. Type `help' for help.

---

### Post by rsambuca on 2007-11-14
What method did you use to install it?

---

### Post by jonpon on 2007-11-14
I installed it with :
sudo apt-get install vlc
After it didn't work even after restart I, sudo apt-get remove vlc
and the repeated sudo....install vlc

---

### Post by rsambuca on 2007-11-14
Have you tried opening a media file with it?

---

### Post by jonpon on 2007-11-14
It's not in the list of "other programs" so I cant try to open a media file.

---

### Post by rsambuca on 2007-11-14
Then use a "custom command" in the Open With section.  Go to the bottom and then browse...  it will be in /usr/bin/

---

### Post by jonpon on 2007-11-14
I tried the "custom command " but nothing happens 
This is really strange, I've used vlc before on a previous installation and it worked fine.

---

### Post by rsambuca on 2007-11-14
What happens when you open a terminal and enter

vlc 'filename'

where 'filename' is the path and filename of one of your media files.  (You can drag a file from Nautilus to the terminal window so you don't have to type the entire path)

---

### Post by rsambuca on 2007-11-14
I have found out that if vlc opens in the remote control interface, then it has been compiled without the gtk-dev packages.  Where did you install it from?  What repos are you using?

Post the output of 

cat /etc/apt/sources.list

---

### Post by tech9 on 2007-11-14
> **jonpon said:**
> I tried the "custom command " but nothing happens 
This is really strange, I've used vlc before on a previous installation and it worked fine.

try this...

sudo apt-get update

then - try

sudo apt-get install vlc 



I had this problem, but after running the install command after an update - that fixed the problem for me   :guitar:

---

### Post by jonpon on 2007-11-14
Thanks very much. I'll try that

---

### Post by tech9 on 2007-11-15
> **jonpon said:**
> Thanks very much. I'll try that

your welcome - good luck

---

### Post by samshi on 2007-11-15
I am also having the same problem here. VLC will not open by clicking it or form the console. I have repeatedly installed and unstalled it but the problem is same.

While installing it gives error regarding clvm or something and redhat things like that.

Can anyone help?

---

### Post by jonpon on 2007-11-15
I've just got vlc to work! I don't know how kosher my method was, I'm no profi but here's how I did it and it worked for me.
I changed my repository from "main" to my local here in Germany
then

CODE:
sudo apt-get remove vlc

then I deleted the hidden vlc file from my home folder (in Home folder, press "cntrl H" then delete the vlc file)

then I logged on as "root" and deleted the archive file from the
 file system/var/cache/apt/archive/vlc
and
 file system/usr/bin/vlc

then I logged on normal again and
CODE:
sudo apt-get install vlc

And now it works

many thanks to 
rsambuca and tech9 for their help

---

### Post by tech9 on 2007-11-16
> **jonpon said:**
> I've just got vlc to work! I don't know how kosher my method was, I'm no profi but here's how I did it and it worked for me.
I changed my repository from "main" to my local here in Germany
then

CODE:
sudo apt-get remove vlc

then I deleted the hidden vlc file from my home folder (in Home folder, press "cntrl H" then delete the vlc file)

then I logged on as "root" and deleted the archive file from the
 file system/var/cache/apt/archive/vlc
and
 file system/usr/bin/vlc

then I logged on normal again and
CODE:
sudo apt-get install vlc

And now it works

many thanks to 
rsambuca and tech9 for their help

Glad to see you got it working :)

---

### Post by samshi on 2007-11-16
I hope it works. I'll give it a try.:)

---

### Post by samshi on 2007-11-16
I did what you said.

1. removed vlc

2. deleted the hidden vlc file from my home folder 

3. deleted the archive file from the file system/var/cache/apt/archive/vlc and file system/usr/bin/vlc

4. installed vlc again.

Now it says "Could not launch menu item > Failed to execute child process "wxvlc" (No such file or directory)"

What can I do please help me.!!!!:(

---

### Post by samshi on 2007-11-16
Hey I went back to Synaptic Package manager and marked "wxvlc" for reinstallation.

Now everything is fine

I think this is the best method. Thanks for the Help.:popcorn:

---

### Post by jonpon on 2007-11-16
> **samshi said:**
> I did what you said.

1. removed vlc

2. deleted the hidden vlc file from my home folder 

3. deleted the archive file from the file system/var/cache/apt/archive/vlc and file system/usr/bin/vlc

4. installed vlc again.

Now it says "Could not launch menu item > Failed to execute child process "wxvlc" (No such file or directory)"

What can I do please help me.!!!!:(

Yes, sorry, In my euphoria I forgot about that wxvlc problem, but it's nice to see you managed it.

---

### Post by Craigus on 2007-11-16
Hmmm. Doesn't work for me - I still get the > Failed to execute child process "wxvlc" (No such file or directory)"

error, even after reinstalling wxvlc.

Edit: However, reinstalling vlc after doing all of that did then work, no idea why.

---

