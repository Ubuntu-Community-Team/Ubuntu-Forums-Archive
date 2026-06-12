---
title: "No control over youtube / iplayer content."
date: 2009-12-10
forum: Multimedia Software
---

### Post by themoodude on 2009-12-10
Hi,

I'm running Ubuntu 9.10 x64. I'm using Firefox 3.5.5 as default, and also have Chrome beta installed. Whenever I browse to youtube (same can be said about bbc iplayer) I am able to load and play videos- they automatically play in youtube. All the controls display correctly; the play/pause buttons, seek bar etc. however I have no control over it. When I click the controls on a youtube video (or those in iplayer) nothing happens. I'm unable to pause, mute, or even fullscreen a video.

Could the issue be with my installation of flash? How can I ensure I have the latest required packages? I've installed the restricted extras package already.

Cheers for any help; I miss iplayer :(

Dean

---

### Post by HappyFeet on 2009-12-10
> **themoodude said:**
> 

Could the issue be with my installation of flash?

Yes, it most likely is. 

First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

---

### Post by themoodude on 2009-12-11
Did that exactly as suggested and still I have no control over youtube or iplayer content. They still appear as should; and youtube still automatically plays. I even get the link hand cursor when hovering over the buttons, but clicking has no action.

---

### Post by themoodude on 2009-12-11
OK; so things work fine in Google Chrome Beta but not Firefox.

---

### Post by Leperous on 2009-12-11
I've seen this problem too on 32 & 64 bit systems (only in Chrome) but it seems to have fixed itself, not sure if it's because I use the unstable Chrome builds or downloaded Flash from the Adobe website rather than the repos :(

Only thing I can suggest is that pressing the spacebar often lets you start/stop video.

---

### Post by themoodude on 2009-12-11
It's incredibly strange now. I can interact with youtube videos on youtube but not when they're embedded in other sites. Still no luck with iplayer though. Also; although they work under Google Chrome, I did have a play with the latest Chromium Browser which didn't work (although I've removed it since).
I may just have to use Chrome for the videos...

---

### Post by marshall.robert on 2009-12-11
I have found on my system when it does this that turning off Compiz sorts it out.

When Compiz is turned off all flash seems to work fine, but when Compiz is on flash based stuff, especially iPlayer, ceases to respond to mouse clicks.

---

### Post by themoodude on 2009-12-11
That's incredibly annoying; I love compiz effects...
Thank you very much for deducing the issue; not entirely sure as to why compiz would interfere in such a way, but I suppose it's one of those things.

---

### Post by themoodude on 2009-12-11
I can confirm that replacing compiz with metacity temporarily does fix it. Youtube (both on site and embedded) along with iplayer now play correctly. It's a shame really; I love Compiz, but I suppose a brief disable won't kill seeing as I'd have the video in iplayer fullscreened anyway.

---

### Post by mahiyar on 2009-12-30
Well you can still use keyboard controls for your player, 
space bar -- pause/start
alt + ->/<- -- for rewind and forward
etc, etc

dunno, search the web for more keyboard controls

---

### Post by stephanvaningen on 2010-02-07
Press Alt-F2:
```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```
Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

---

### Post by lmellor on 2010-05-01
what exactly does this do? I have found it work flawlessly, just wondered exactly what I changed.

---

