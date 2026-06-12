---
title: "Unable to use flash uploaders for multimedia"
date: 2011-03-24
forum: Multimedia Software
---

### Post by kopiluac on 2011-03-24
Hi All,
I'm new to Ubuntu, so apologize if this question has already been addressed. I did check the forums and have searched extensively using Google to find an answer, before posting here. 

Anyway, I'm using* Ubuntu 10.10 on a 64bit OS with Firefox 4* browser. I've also tested this issue using the previous stable version of FF with my Ubuntu platform. 

**Here are my issues:** First, I am unable to print multiple pages from websites which utilize flash. The larger concern, however, is the fact that I'm unable to upload either audio or video to a server which uses flash uploading. I assume this has something to do with adobe flash plugin for Firefox, but all my fixes have been in vain. Perhaps that's not the issue after-all. 

Any help is greatly appreciated. 

Thanks so much.

---

### Post by no2498 on 2011-03-25
have you set the sites you use to allow and remember
in the adobe settings manager
you can do it at the adobe site

---

### Post by kopiluac on 2011-03-25
No. I haven't. Pardon my ignorance, but I don't even know what you're talking about. Please clarify. In the meantime, I'll visit the Adobe site and see if I can figure out what you mean about "allowing" certain sites. I didn't even know Adobe had anything like that to manage permissions or anything else. I'll take a gander. Thanks for the reply.
Kopi

---

### Post by no2498 on 2011-03-26
as for fire fox you may need to get the plugin flash aid and run it
it gets you the new flash player

---

### Post by kopiluac on 2011-03-27
Thanks for the reply. I tried everything you listed without success. I checked the adobe settings and frankly, I don't think those parameters are related to this problem. 

Also, dl'd the add-on you recommended for FF and ran it, but the problem still persists: Every time I try to upload an mp3 to the server, my system just lies there not doing anything...no progress bar, nothing. I'm really, really frustrated at this point. I've been at this for well over a week without success...searching the forums, searching the web, trying one thing after another and coming up empty. I guess it's a good thing I've got windows on the other partition so I can get my work done. 

Sorry if this last communication sounds a bit angst laden. Several days of beating your head against a wall trying to get your system to do something which should be a relatively simple endeavor...well...it does things to you, man. Seems like a lot of irony. There's so much to love about Linux and so precious little to love about windows and yet, I'm forced to use microsoft's crapware OS to perform this basic operation...and I thought I was kissing windows goodbye. I hang my head in shame...

---

### Post by no2498 on 2011-03-28
i use 32 bit but i had to install grease monkey plugin to get fire fox to let me use flash

---

### Post by kopiluac on 2011-03-28
Thanks. I've installed the plugin and I'm reading the documentation on it now. It says that Grease Monkey will not work without scripts. Can you tell me which script you used to get flash uploading functional. In lieu of your reply, I'll be checking the script site listed for users in the documentation. Hopefully, I'll find what I'm looking for. However, you can save me a lot of legwork if you tell the script you employed with the Grease Monkey extension. 

Cheers

---

### Post by kopiluac on 2011-03-30
I assume the ominous silence means that you don't know what script to use. I couldn't find one either. I'm not even sure there is one. 

I have discovered something else, though, since our last communication. The problem with uploading media exists when using Chromium as well. It behaves exactly the same as with FF 4. Some of the buttons work, and I can see all the control options for the flash uploader on the third party server, but when you push the "upload" button, although it says it's uploading, nothing happens. It just hangs with no progress bar and no upload whatsoever. Any other thoughts? I'm out of ideas here. 

Thanks.

---

### Post by no2498 on 2011-03-30
i did not use any scripts 
only other thing i can think of is to try opera browser 
and you may chase down lovinglinux hes good with this kind of things

---

### Post by kopiluac on 2011-03-30
Okay, fine. How can I track this guy down? This problem has plagued me since I installed ubuntu 10.10 going on two weeks now. I have long since gone past the point of desperate. The thought of going back to windows or even keeping windows as my mistress conjures up images of me downing several bottles of Maalox, Pepto, and pass the Rolaids...quick. Not a comforting thought. Thanks for trying to help me out of this jam.

Best,

Kopi

---

### Post by no2498 on 2011-03-30
id send him a privet massage 
as to not take over his sticky 

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by SeijiSensei on 2011-03-30
I'm afraid no2498 doesn't understand your question.  All his or her answers have to do with viewing Flash videos using the Adobe plug-in.

> The larger concern, however, is the fact that I'm unable to upload either audio or video to a server which uses flash uploading.

I must admit I've never heard of a "Flash upload" before.  Is this a public server so others of us might see what's involved?  Any documentation from Adobe we could look at?  In particular documentation for the server end of this connection?

Have you done this before in Windows?  Using Firefox on Windows?  If it worked with IE, there might be some type of proprietary software like an ActiveX control that's required to do this.

I assume we're not talking about YouTube here.  I've had no trouble uploading files in an acceptable container to them using Firefox on Linux, but Flash isn't involved in that transfer at all.

---

### Post by kopiluac on 2011-03-30
This isn't a public server where you can access the media uploader without login credentials. Basically, the uploader is flash based. That's what I mean when I say "flash uploader." Probably not the correct term. Some of the buttons work, and I  can see all the control options for the uploader on the server. But when you push the "upload" button, although it says  it's uploading, nothing happens. It just hangs with no progress bar and  no upload whatsoever. 

It works on windows using firefox 3.6 with no issues. When I ported over to Ubuntu 10.10, I used the same FF browser, but found I was unable to upload any media to the server. Later, I upgraded to firefox 4, with no change in this behavior. I've also tested this on Chromium with the same result. 

I have not tested this on YouTube yet. But, I've uploaded mp3 and flv files to my own webserver using Cpanel interface with no issues at all.

The site which is giving me all the trouble is called sermonstudio.net. Any help is appreciated. 

Thanks:)

---

### Post by lovinglinux on 2011-03-30
> **kopiluac said:**
> This isn't a public server where you can access the media uploader without login credentials. Basically, the uploader is flash based. That's what I mean when I say "flash uploader." Probably not the correct term. Some of the buttons work, and I  can see all the control options for the uploader on the server. But when you push the "upload" button, although it says  it's uploading, nothing happens. It just hangs with no progress bar and  no upload whatsoever. 

It works on windows using firefox 3.6 with no issues. When I ported over to Ubuntu 10.10, I used the same FF browser, but found I was unable to upload any media to the server. Later, I upgraded to firefox 4, with no change in this behavior. I've also tested this on Chromium with the same result. 

I have not tested this on YouTube yet. But, I've uploaded mp3 and flv files to my own webserver using Cpanel interface with no issues at all.

The site which is giving me all the trouble is called sermonstudio.net. Any help is appreciated. 

Thanks:)

Hi,

I am looking at the site right now and there is a free plan I can use to test. Is the registration automatic, or they do human verification and approval?

---

### Post by lovinglinux on 2011-03-30
I did some tests and I was able to upload using:

Firefox 4 | Linux Mint KDE 10 32bit | Shockwave Flash 32bit v10.3 d180 Beta
Chrome 10.0.648.204 | Linux Mint KDE 10 32bit | Shockwave Flash 32bit v10.3 d180 Beta
Opera 11.01 | Linux Mint KDE 10 32bit | Shockwave Flash 32bit v10.3 d180 Beta

Firefox 3.6.15 | Ubuntu Karmic 64bit | Shockwave Flash 64bit v10.3 d180 Beta
Firefox 3.6.15 | Ubuntu Karmic 64bit | Shockwave Flash 32bit 10.2 r152 Stable

So I suspect is not a flash or browser problem, but a network problem.

Try to disable ipv6. To do that, open the file /etc/default/grub with an editor:

```
gksudo gedit /etc/default/grub
```

Then replace the following line:

```
RUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```

With the following line:

```
GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash”
```

Then update grub:

```
sudo update-grub
```

Just to make sure, go to Flash-Aid help tab, generate a report and paste the contents of the *firefox-report.txt* file created in your desktop.

---

### Post by kopiluac on 2011-03-30
**After the the first command, I got this reply:**[INDENT](gksudo:3297): Gtk-WARNING **: Unable to locate theme engine in module_path: "ia_ora",
/usr/share/themes/win7-gtk/gtk-2.0/gtkrc:844: Unable to locate image file in pixmap_path: "Panel/panel-bg-30px.png"
(gedit:3299): Gtk-WARNING **: Unable to locate theme engine in module_path: "ia_ora",
/usr/share/themes/win7-gtk/gtk-2.0/gtkrc:844: Unable to locate image file in pixmap_path: "Panel/panel-bg-30px.png"

[/INDENT]**After editing the file, saving and running sudo update-grub, I got this:**[INDENT]/etc/default/grub: 9: quiet: not found
[/INDENT]I had to attach the Flash-Aid report you requested, as the editor wouldn't allow me to paste it due to all the character sets getting converted to smilies after pasting (Sorry). Wouldn't let me submit the data that way, as each one counts as an image and I had exceeded the number allowable. Weird.

---

### Post by lovinglinux on 2011-03-31
> **kopiluac said:**
> **After the the first command, I got this reply:**[INDENT](gksudo:3297): Gtk-WARNING **: Unable to locate theme engine in module_path: "ia_ora",
/usr/share/themes/win7-gtk/gtk-2.0/gtkrc:844: Unable to locate image file in pixmap_path: "Panel/panel-bg-30px.png"
(gedit:3299): Gtk-WARNING **: Unable to locate theme engine in module_path: "ia_ora",
/usr/share/themes/win7-gtk/gtk-2.0/gtkrc:844: Unable to locate image file in pixmap_path: "Panel/panel-bg-30px.png"

[/INDENT]**After editing the file, saving and running sudo update-grub, I got this:**[INDENT]/etc/default/grub: 9: quiet: not found
[/INDENT]I had to attach the Flash-Aid report you requested, as the editor wouldn't allow me to paste it due to all the character sets getting converted to smilies after pasting (Sorry). Wouldn't let me submit the data that way, as each one counts as an image and I had exceeded the number allowable. Weird.

When you executed Flash-Aid, did you see a terminal asking for your password? You have multiple flash installations, that should have been removed by Flash-Aid.

Anyway, go to "System >> Administration >> Software Sources >>> Other Software" and then delete the entry with "sevenmachines" in it. Then execute Flash-Aid again and make sure the script is executed in a terminal without errors. Then generate a new report.

---

### Post by kopiluac on 2011-03-31
Just finished implementing your instructions. Flash Aid executed in terminal and I didn't see any errors when it did. I checked the latest firefox report (attached) and it looks like there are errors on there. While I wait for further instructions, I'll go and test on sermonstudio's server again. Thank you for your continued assistance.

**UPDATE!!!!!**
This time when I went to sermonstudio, I was able to get the file uploaded. It was a bit dicey, though, as each time I had to upload twice before the file would transfer. In both instances, I would hit the upload button (and nothing would happen). Next, I would cancel the upload, wait for the page to refresh and then hit the upload button again. After doing so, the file would, then, upload normally. In a perfect world, I'd like to have it work on the first try, but under the circumstances I'm delighted that I can, at least, get the file transferred now, even if it takes a bit of arm twisting to get the job done. If you think you can help me resolve this so it transfers on the first click, then I'd love for you to continue working this problem with me. If not, that's okay too. Let me know how you'd like to proceed and, of course, many thanks for your kind and patient assistance.

---

### Post by lovinglinux on 2011-03-31
> **kopiluac said:**
> Just finished implementing your instructions. Flash Aid executed in terminal and I didn't see any errors when it did. I checked the latest firefox report (attached) and it looks like there are errors on there. While I wait for further instructions, I'll go and test on sermonstudio's server again. Thank you for your continued assistance.

Weird. Although Firefox is recognizing the latest beta 64bit version of flash, the 32bit is still installed. I don't know why. Are you disabling flash removal in the extension?

Please execcute this on a terminal:

```
sudo apt-get get remove flashplugin-installer
```

---

### Post by kopiluac on 2011-03-31
Here's the reply after running the command:
The following packages were automatically installed and are no longer required:
  mesa-utils libglew1.5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 229kB disk space will be freed.
Do you want to continue [Y/n]? 

After entering "Y", I  got this:
(Reading database ... 184734 files and directories currently installed.)
Removing flashplugin-nonfree ...
Removing flashplugin-installer ...

---

### Post by no2498 on 2011-03-31
kopiluac told you lovinglinx was good 
glad you got it working
thanks lovinglinux

---

### Post by lovinglinux on 2011-03-31
> **no2498 said:**
> kopiluac told you lovinglinx was good 
glad you got it working
thanks lovinglinux

Thanks. 

:popcorn:

---

### Post by lovinglinux on 2011-03-31
> **kopiluac said:**
> **UPDATE!!!!!**
This time when I went to sermonstudio, I was able to get the file uploaded. It was a bit dicey, though, as each time I had to upload twice before the file would transfer. In both instances, I would hit the upload button (and nothing would happen). Next, I would cancel the upload, wait for the page to refresh and then hit the upload button again. After doing so, the file would, then, upload normally. In a perfect world, I'd like to have it work on the first try, but under the circumstances I'm delighted that I can, at least, get the file transferred now, even if it takes a bit of arm twisting to get the job done. If you think you can help me resolve this so it transfers on the first click, then I'd love for you to continue working this problem with me. If not, that's okay too. Let me know how you'd like to proceed and, of course, many thanks for your kind and patient assistance.

I am glad it worked. I really don't know why it doesn't upload in the first try.

---

### Post by kopiluac on 2011-03-31
> I am glad it worked. I really don't know why it doesn't upload in the first try. 	

I don't know why either. All I know is it wouldn't do anything before and since we made all your suggested changes, it, now, works:guitar:


I'm a very happy man right now. Thanks so much for helping me to resolve this. Couldn't have done it without you. 

YOU ROCK! 

Will mark this thread "SOLVED"

---

### Post by lovinglinux on 2011-03-31
> **kopiluac said:**
> I don't know why either. All I know is it wouldn't do anything before and since we made all your suggested changes, it, now, works:guitar:


I'm a very happy man right now. Thanks so much for helping me to resolve this. Couldn't have done it without you. 

YOU ROCK! 

Will mark this thread "SOLVED"

You are welcome.

---

### Post by encefalocardia on 2011-04-11
This is happening for me on Gmail. The flash uploader it's not loaded.

---

### Post by kopiluac on 2011-04-11
This thread is marked as solved. Probably, you'll need to start a new thread as I don't think anyone is watching this one anymore. 

Also, be sure to outline in graphic detail the nature of your problem in gmail, i.e. the exact nature of the issue and everything you're doing when the problem arises. That way, whoever ends up helping you can try to reproduce the issue themselves when they troubleshoot. 

Good luck:)

---

