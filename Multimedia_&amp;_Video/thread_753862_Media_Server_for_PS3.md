---
title: "Media Server for PS3"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by thestig_992 on 2008-04-13
Hey everyone, im having some trouble getting my ubuntu gutsy to act as a media server so that I can stream video directly to my PS3. So far I've tried using VLC (which failed miserabley) and now I've downloaded Mediatomb, but Im having some problems running it. Firstly, it doesnt appear in the applications drop down bar, so i;ve tried running it in the deskbar applet (the searching tool), which works as it should, but no Mediatomb window opens. Under system monitor it says that there is a process called mediatomb running, but other than that I have no idea what to do, as Im kinda new to linux...

Alo, im happy to get any new program to help me stream media, so if you have a reccomendation for a different program, it would be greatly appreciated..as well as a short guide as to how to set it up...
Thanks

---

### Post by amak79 on 2008-04-14
thestig_992,

You can start MediaTomb as a daemon or manually on the command line which is essentially what the deskbar applet does. I recommend starting MediaTomb as a daemon so that it will start every time Ubuntu boots. You will need to stop any existing MediaTomb processes via **sudo killall mediatomb**. Now open **/etc/default/mediatomb** and make sure that the **NO_START** variable is set to an empty string. You can now start MediaTomb via **sudo /etc/init.d/mediatomb start**. Now open **/var/lib/mediatomb/mediatomb.html** in your web browser. This is the MediaTomb web based user interface which allows you to easily add your media files. If you want to configure MediaTomb then you will need to edit **/etc/mediatomb/config.xml** and restart MediaTomb after any changes.

---

### Post by matt_s_lon on 2008-04-14
thestig_992,

I've recently spent some time fiddling with Mediatomb trying to get it to serve to my Ps3 from a gutsy gibbon box: I run it from the terminal with the command mediatomb, then when it loads up, it shows you (amongst other things) the ip address and port mediatomb is serving from. If you right click the ip address in the terminal window you can follow it as a link which'll also take you straight to the web interface. This is useful as sometimes MT uses a different port to serve from.

You could also try fuppes [http://fuppes.ulrich-voelkel.de ]("http://fuppes.ulrich-voelkel.de")to serve media to a PS3, which is apparently thinner and thus faster than Mediatomb, although this is can be a slightly complex compile / install / configure.

Personally I found that mediatomb would serve fine, but video was a bit jumpy (not quite got to the bottom of this yet) - I used to serve from an XP box using a tool called Simplecenter. This used to work fine with video but take an age to start up, then prevent my XP box from doing anything else whatsoever.

Hope this helps.:)

---

### Post by Posterus on 2008-04-17
> **matt_s_lon said:**
> 

Personally I found that mediatomb would serve fine, but video was a bit jumpy (not quite got to the bottom of this yet) - I used to serve from an XP box using a tool called Simplecenter. This used to work fine with video but take an age to start up, then prevent my XP box from doing anything else whatsoever.

Hope this helps.:)

Might I suggest using Pimpstreamer for your XP box?  [www.pimpware.org](www.pimpware.org) I believe is the website.  It is a great stream program using the DLNS protocol so it connects fine with your ps3 and is also very light weight and does not render your XP useless =] also video runs very smoothly

---

### Post by KillaB7 on 2008-04-25
How about a non-streaming (just file sharing) solution?

I have TVersity working from my laptop (XP Pro), but I'd love to get this going in Ubuntu.  If it takes upgrading to Hardy then great.  I'm going to be doing that soon anyway :)

---

### Post by amak79 on 2008-04-29
KillaB7,

The PS3 only supports streaming via DLNA so file (SMB) sharing is not possible, although I wish it was. I believe your best option on Linux is to use MediaTomb.

---

### Post by KillaB7 on 2008-04-30
amak79,

Thanks for the reply.  Using TVersity I was able to copy files directly to the PS3 without streaming/transcoding.

I just installed MediaTomb on Hardy and it's seen by the PS3.  Does it have to be set up to stream/transcode or can it function like TVersity and I'm assuming WMP11?

---

### Post by amak79 on 2008-04-30
KillaB7,

MediaTomb does need to be setup when using the PS3, and depending on whether your media is supported by the PS3, you might need to enable transcoding.

If you started MediaTomb on the command line as your user then you need to edit **~/.mediatomb/config.xml**, or if you started MediaTomb as a service then edit **/etc/mediatomb/config.xml**.

You need to make sure that the **protocolInfo** tag **extend** attribute is to **yes**: **<protocolInfo extend="yes"/>**. Now restart MediaTomb and import your media via the MediaTomb web interface. Again if you started MediaTomb as a service open the file **/var/lib/mediatomb/mediatomb.html** which is a bookmark to the web interface. If you started MediaTomb as your user then open **~/.mediatomb/mediatomb.html**.

---

### Post by KillaB7 on 2008-05-01
My XviD files where showing up on the PS3 as "unsupported data" so I followed this guide and I can't believe how easy it was to configure: [http://ubuntuforums.org/showthread.php?t=650020](http://ubuntuforums.org/showthread.php?t=650020)

Started on Step 2 after downloading the pre-compiled gutsy debs from mediatomb's site.

Big thanks to mrhorrible78 and amak79!

---

