---
title: "Can't get k9copy to work right out of the box!"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by discmaster on 2007-05-30
Trying to use k9copy, & first thing I get is; "can't open disc /dev/hdb". If I click on the dvd copy icon, I get "DVD is not opened". I checked computer; r/click dvdr drive to try to mount it, & I get "unable to mount media" - There is probably no media in the drive.

This is the first time I am using this, I just installed from synaptic; I don't know if I need to configure further, need to add more to it, what to do?

---

### Post by lawr_rawr on 2007-05-30
Try browsing to /media and selecting cdrom<number> as your input source. K9Copy defaults to /dev/hdc for me, but I can select the DVD drive under /media.

---

### Post by discmaster on 2007-05-30
Well, I need more help than that now... After reading several other threads on similar k9 issues, I decided to reboot w/ the media in the drive. After rebooting, it was mounted, & titles did open up in k9copy.

Now - I couldn't get the preview to work, so I was poking around in the options/etc., & I enabled openGL. k9copy then crashed, & all attempts to get it to open now simply results in a crash & the pgm. closes again.

What's next? :(

---

### Post by discmaster on 2007-05-30
Just found [this]("http://ubuntuforums.org/showthread.php?p=2507513&highlight=k9copy#post2507513") thread! That fixed the open GL issue. Now, back to the preview problem...

---

### Post by discmaster on 2007-05-30
Anyone know how to get the preview function to work?

Also, is there a tutorial anywhere on this pgm.? I can run all the others in windows. (shrink/dvdd, etc.) but I can seem to get k9copy to do anything :confused:

---

### Post by discmaster on 2007-05-31
After trying unsucessfully with dvdd/shrink, I am back here ytrying my luck with this one again...

How do I get the dvd drive "mounted"? When I click on the drive to mount it, I get "Unable to mount media" - There is probably no media in the drive. (which there is)

---

### Post by discmaster on 2007-05-31
Can't get preview function to work?

Can I open ripped files with this program, i.e. files  that I already ripped dvdd?

---

### Post by discmaster on 2007-05-31
found this on another thread;
> I had the same problem, but I figured it out. You have to highlight the "Title !" or similar text (not "Titleset 1") and then click the button shaped like a camera. The tooltip says "Play title". See if that works.


That does make the preview function work, but the resulting preview still has all the copy protection on it; i.e., "green/snowy" picture.

Will this pgm. not do a copy? I was under the impression that it would; btw, this is an older title of mine that I am backing up, no fancy protections on this one.

---

### Post by discmaster on 2007-06-05
Okay, I loaded the backup files from the HD, went thru & selected the items I wanted to get rid of, & I now want to save as an iso file for later burning.

How do I do that? I do not see any button to click on to start the process. The only thing I see is create mpeg 4, which is not what I want (divx)?

I just need a plain ol' ISO file... how do I get it?

---

### Post by discmaster on 2007-06-05
UPDATE: After clicking on "COPY" it looks as if that will give me what I want, an ISO file.

NOW - After selecting the folder where I want it to go, I get an error;

> AN error occured while running DVD Author - ERR: Error reading from pipe: No such file or directory

---

### Post by discmaster on 2007-06-05
This is where I get stuck at; What do I put in the location box?

[[IMG]http://img117.imageshack.us/img117/5158/kangjack1ss7.png[/IMG]](http://imageshack.us)

---

### Post by discmaster on 2007-06-05
Please help, anyone? I've clicked on every button, looked at all the preferences, I do not see how to create an ISO - does anyone have any idea how to do this?

---

### Post by discmaster on 2007-06-10
:frown:     Any help as per question in post # 11? I am tearing my hair out here trying to make this work!!!    ](*,)    :confused:

---

### Post by bitumen on 2007-07-01
got it working its midnight now im off to bed will update this post tomorrow when i figure out what i did :p

tell you what i finally got:

no initial menus 
auto start 
chapter selection : By skipping through the chapters
subtitles selection: off, English [1]  (commentary)
language selection: off, English[1] (film sound track), English[2] Commentary 

best of all No green snow

I'm new at this and only been using Linux 2 days so don't except a compete "how to" and be patient with me!
it'll be what i did to get what I wanted!

Big thank you to all the previous post's  as they helped me get it working :)

so night for now


**tested dvd and only works sometimes so Im still trying to figure this thing out **

check this thread for ideas!

[http://ubuntuforums.org/showthread.php?t=424256]("http://ubuntuforums.org/showthread.php?t=424256")

---

