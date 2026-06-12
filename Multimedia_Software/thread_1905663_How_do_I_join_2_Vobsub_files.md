---
title: "How do I join 2 Vobsub files?"
date: 2012-01-07
forum: Multimedia Software
---

### Post by mrsfixit on 2012-01-07
All I want to is to join 2 sets of idx/sub files.

I used to do this easily in Windows with [Vobsub]("http://www.videohelp.com/tools/VobSub")'s subtitle joiner, I cannot for the life of me figure out how to do it in Linux. I use Ubuntu 10.04.

I have several subtitle applications in Ubuntu, none of them will work with anything other than text based subs.

I don't want to extract, convert, embed into the video- all I want to do  is take vobsub set #1, and append vobsub set #2 to the end of it-  period. That's all.

I've tried installing Vobsub under Wine and that didn't work either.

Can anyone please help me out with this?

Any help appreciated. [IMG]http://forum.videohelp.com/images/smilies/smile.gif[/IMG]

---

### Post by mrsfixit on 2012-01-11
No answers at all?

Nobody knows how to do this? Seriously? There is no way?

This is disappointing that such a simple task cannot be accomplished in the OS of my choice.

---

### Post by xc3RnbFO8P on 2012-01-11
Maybe this will help:
[http://en.flossmanuals.net/avidemux/ch019_extract-dvd-subtitles/]("http://en.flossmanuals.net/avidemux/ch019_extract-dvd-subtitles/")

---

### Post by Buntumatic on 2012-01-11
[http://home.gna.org/subtitleeditor/](http://home.gna.org/subtitleeditor/)

Check out this one, perhaps it can append files.

---

### Post by mrsfixit on 2012-01-11
> **Buntumatic said:**
> [http://home.gna.org/subtitleeditor/](http://home.gna.org/subtitleeditor/)

Check out this one, perhaps it can append files.

Nope, I have that one and it only works with text based subs.

Thanks for replying though. :P

---

### Post by mrsfixit on 2012-01-11
> **Ringi said:**
> Maybe this will help:
[http://en.flossmanuals.net/avidemux/ch019_extract-dvd-subtitles/](http://en.flossmanuals.net/avidemux/ch019_extract-dvd-subtitles/)

No, this doesn't really help either. I don't need to extract the subs, they're already extracted. And this method is for conversion from idx/sub to srt text based subs, which is time consuming and generally a PITA.

Thank you for replying though.

I guess I'm going to have to keep a Windows machine around just for this purpose. 

At this point I wish I knew how to write my own program... LOL :)

---

### Post by Buntumatic on 2012-01-11
Maybe mkvtoolnix can do it ... it will mux into mkv indeed.

---

### Post by mrsfixit on 2012-01-12
> **Buntumatic said:**
> Maybe mkvtoolnix can do it ... it will mux into mkv indeed.

I don't use mkv files, I use avi's. And I'm not looking to mux the subs into the video, but thanks anyway for the suggestion. :)

---

### Post by mrsfixit on 2012-11-16
> **mrsfixit said:**
> All I want to is to join 2 sets of idx/sub files.

I used to do this easily in Windows with [Vobsub]("http://www.videohelp.com/tools/VobSub")'s subtitle joiner, I cannot for the life of me figure out how to do it in Linux. I use Ubuntu 10.04.



Through trial and error, I have solved this problem.

I will post this tutorial of how I did it. I have done this on my desktop, which currently runs Ubuntu 10.04, and my notebook, which currently runs Xubuntu 12.04

First of all, you need to install the Windows program "Vobsub". The last version is 2.23. This will work under WINE, even though it has a couple of bugs.

It took a LOT of tinkering to get Vobsub to work correctly. You will also need a couple of files from a Windows install of Vobsub. Also note that newer versions of WINE have a 32 bit and 64 bit folder, so you might need to copy everything to both. Like I said, I did this by trial and error, with a lot of hair pulling, cursing, screaming, throwing things and tantrums in the process... LOL :P

VobSub- installing under WINE:

1. Make sure the VobSub 2.23 exe is marked as executable.

2. Right click, open with Wine program loader.

3. Install.

Issues:

VobSub will **NOT** launch until the following steps are taken.

1. Go to the Wine Windows System32 folder, and find the file "DVobSub.ax". Right click, properties, mark as executable.

2. Copy the Windows DLL "MFC42U.dll" from Windows, and paste it into the Wine Windows System32 folder. Right click, properties, permissions, mark as executable.

3. In the WINE programs folder, I also marked the "submux.exe" and "subresync.exe" as executable.

******NOTE******

Newer versions of WINE now have a sytem32 AND a system64 folder.

In Xubuntu I had to copy everything into **BOTH** folders and mark them executable to get it to work.

**_Now for the joining part:_**

**********NOTE**********

You need to know the join point of the 2 sets of idx/sub files, because Vobsub will need this. Vobsub fills in the timecodes at the bottom of the window, but I find them to be wildly inaccurate, so I put in the correct ones by looking at where the first video ends.

To find this open the first video file- ie: video 1.avi in a video editor such as AviDemux.

Look at the bottom, and you will see the exact length of the video- ie: 00:56:45:707. That's just an example. **I always add 1 ms to the last number**- so then the example would read: 00:56:45:_**708**_.

If you don't know how to use Vobsub it's pretty simple.

Open Vobsub. For "input 1" select your first idx file. For input 2 select your second idx file. For output- name the file so that it matches the avi file it goes with, which if you haven't done it already- your 2 avi files will need to be joined using Avidemux. Fill in the correct timecodes in the boxes at the bottom of the window.

Vobsub will create **one** new idx/sub set from the 2 sets you put in. It only takes a few seconds to do it, and there isn't any confirmation dialogue to tell you it's done. If you see the new idx/sub set appear in your directory, it's done and you can exit the program.

*******NOTE*******

I have found Vobsub to be a bit buggy, and it sometimes will not launch. I have experienced this particularly after already using it once. If I try to launch it a second or third time it may or may not work. YMMV. 

Logging out and back in again usually solves the problem.

Open the newly created idx file in gedit. I have found ONLY gedit works for this, I had to install it in Xubuntu to get this trick to work. I tried several other text editors with no luck, so stick with gedit.

VobSub will put in a character that looks like an **"R"** in a circle.

Highlight the symbol, then go to "Search/Replace". 

Click on "Replace All", but **don't** put anything in the "Replace With" box.

Save the file, close the file, then re-open the file again with gedit.

Go to "save as" and choose character encoding as "Western (ISO-8859-15)", and line ending as "Windows" then resave the file again.

It should now work.

To be sure, try opening the idx with  a really basic text editor like Mousepad or Leafpad. If it opens normally and shows the subtitle texts and doesn't show only a few garbage characters then it's ok.

**Quick info on joining 2 avi's in AviDemux, it's very simple:**

Open  video #1. Go to "File/Append" and select video #2. Click "Save", give  it a name, and answer "yes" to the 2 dialogs that come up next. That's  it.

***********************************************************

This drove me absolutely freaking nuts until I figured it out. Why there is only ONE program in existence that works with Vobsubs I don't know. If I knew how to code, I would create one for Linux, but that is waaaay above my ability.

I hope this information helps some other poor soul tearing their hair out trying to do the same thing, because I'm sure I can't be the only one who needed this functionality in Linux.

---

