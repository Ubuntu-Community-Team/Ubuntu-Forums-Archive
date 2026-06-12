---
title: "How do i get my dvds to play?"
date: 2009-02-07
forum: Multimedia Software
---

### Post by Macfunky on 2009-02-07
I have installed the ubuntu restricted drivers and still nothing. I am using VLC player as i am accustomed to using it. I also installed some codecs via the command line. Found the directions online. Cant remember what they were called tho. I have had ubuntu on another desktop and after installing all the codecs i have already installed on this computer, dvds were playing perfect. Any ideas on what im missing?

EDIT: The following are what i have installed -
libdvdnav4,
libdvdread3
gstreamer0.10-plugins-ugly 

I also installed the libdvdcss2 package via the terminal. I dont know what else i need to do as i had it working fine with those on another desktop. The dvd-rom is working fine as its the one i used in the other desktop. Any ideas?

---

### Post by redroad55 on 2009-02-07
have you installed the medibuntu repository ?
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

Also check against this guide what you still need to install:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
Post back..best to you

---

### Post by Bablefish on 2009-02-07
I agree about Medibuntu, without that your not going to play anything. But please keep in mind Automatrix if all else fails.

---

### Post by Macfunky on 2009-02-08
Hi guys. Thanks for the advise. I wont be back to my computer until 2moro but ill be sure to let you know if that fixes my problem. I will post my success or otherwise up on here. Thanks again

---

### Post by issih on 2009-02-08
Chances are you need the libdvdcss2 package from the medibuntu repositories:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Have a bit of a read of that..

Hope that helps

---

### Post by ohgodnotanother1 on 2009-02-09
You don't need to install all those "stupid" codecs as VLC has them integrated. What you need is the libdvdcss2 package.

After you installed it, execute the following script to set up the DVD decrypter:
/usr/share/doc/libdvdread3/install-css.sh

That should output some lines and you should be fine playing your DVDs.
You don't need Medibuntu and all the codecs it contains, for this.

---

### Post by howefield on 2009-02-09
> **Bablefish said:**
> But please keep in mind Automatrix if all else fails.

What is Automatrix, and why should it be kept in mind ?

---

### Post by issih on 2009-02-09
Automatix is a little tool that automates adding various repositories to the sources of the package manager, and installing various packages that add functionality that ubuntu, for various legal/historical reasons doesn't ship with. Things like flash playback, windows codecs, mp3/dvd support and other bits and bobs.

There were a few of these 3rd party tools in the early years of ubuntu (easy ubuntu and automatix being the most well known). Mostly their use is now not necessary and is considered a bad idea as they tend not to uninstall cleanly and there were various issues upgrading to a newer distribution after using one of them.

Nowadays I think the general advice is to use ubuntu restricted extras and the medibuntu repositories to install non-free/legally challenged code.

Hope that helps

---

### Post by howefield on 2009-02-09
Yeah, perhaps I needed a smiley in my post, I know what Automatix is (or more accurately, was).

I wondered what "Automatrix" was and why it should be kept in mind seeing as it (Automatix) is no longer available.

---

### Post by Macfunky on 2009-02-11
UPDATE: I tried all the mentioned solutions. Still not working at all. I insert a DVD and just as it opens in VLC the screen disappears. I cant figure this one out

---

### Post by redroad55 on 2009-02-11
Read this thread through and try post #3 :
[http://ubuntuforums.org/showthread.php?t=1065475]("http://ubuntuforums.org/showthread.php?t=1065475")
Post back with any results and or questions Best to you

---

### Post by johnjohn2 on 2009-02-11
> **ohgodnotanother1 said:**
> You don't need to install all those "stupid" codecs as VLC has them integrated. What you need is the libdvdcss2 package.

After you installed it, execute the following script to set up the DVD decrypter:
/usr/share/doc/libdvdread3/install-css.sh

That should output some lines and you should be fine playing your DVDs.
You don't need Medibuntu and all the codecs it contains, for this.

Beat me to it:shock:

---

