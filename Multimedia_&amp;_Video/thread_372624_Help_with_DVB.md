---
title: "Help with DVB"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by deeppurple on 2007-02-28
Hi ,

I have worked hard over the last two weeks to get UBUNTU installed on my laptop and get the wireless working. I have a freecom usb dvb stick which again I seem to have working as it will scan and find channels BUT when I click on DVB or GO in kaffeine the whole system hangs completely and I have to reboot. I think its when XINE is initialising but as I'm no linux expert I'm not sure..

What can I check ?, should I be using kaffeine etc..

PLEASE experts give me some ideas

Thanks

---

### Post by deeppurple on 2007-03-01
Is there no-one out there that can help.

I moved to ubunut as I heard so much about it but I'm not getting any answers..

I tried loading KDE instead of gnome and that made no difference either...

As I said Kaffeine finds the channels but when I click on any of them it says XINE INIT... at the bottom of the screen and then hangs

---

### Post by deeppurple on 2007-03-01
I've tried posting this i the multimedia forum but with no replies ( twice! ) so I thought I would try a different forum to see if I could some replies

I installed UBUNTU on my laptop, got wireless working and then tired to get my freecom usb dvb stick working. Using Kaffeine it will scan and find channels BUT when I click on DVB or GO in kaffeine or click on one fo the channels the whole system hangs completely and I have to reboot. 

I tried loading KDE instead of gnome and that made no difference either...

As I said Kaffeine finds the channels but when I click on any of them it says XINE INIT... at the bottom of the screen and then hangs

H E L P !!

---

### Post by DoctorMO on 2007-03-01
Firstly, try pressing [ctrl]+[alt]+[backspace] to restart Xwindows instead of restarting the kernel. it's very unlikely the kernel died and more likly that it's a video driver problem.

Most video viewers for TV use Extra Buffers in the video card which requires some of the proprietory drivers, this is so the video is smooth regardless of the activity of the computer.

It can crash xwindows which is a real pain; best sugestion is to update the video card drivers; if you have a vga only video card then you may have to buy a new one although they havn't been sold since 1996 or so.

---

### Post by deeppurple on 2007-03-01
Thanks for that.. you can tell I am a windows guy cant you !! used to system crashes !

The system is installed on a Toshiba Tecra 8000 which has been featured for other drivers in the forum before and obviously I cant upgrade the video card... It plays all the games ( pingus etc ok ) so whats different about TV video ?

Can I unistall xine and install it again ?

Thanks

P.S. Which is better Gnome or KDE ?##

---

### Post by DoctorMO on 2007-03-01
This thread should be in the support forum, but since you've had no luck there...

Well it sounds like your video card has the drivers installed at least.

you could try other tv programs, I know I settled on tvtime in the end because it just seems to have better features. although I had a Brooktree card which are trivial to get working.

Neither Gnome or KDE is better, install them both and login to each one and see which one you like and deinstall the one you don't.

---

### Post by bapoumba on 2007-03-01
@ deeppurple : I've merged your thread in "Cafe" with your previous one, and edited the main title to make it the same as the "Cafe" thread. Support questions should not be in "Cafe" ;)
When you do not get answers, bumping the thread a couple times in a day is okay. It is also better to choose an informative title.

---

### Post by panch0 on 2007-03-02
Also try KPlayer which is another player that supports DVB but uses MPlayer as the backend rather than Xine, and so usually gives better results.

---

### Post by deeppurple on 2007-03-03
Thanks for all the suggestions.

I'm going to try once more today after which I'll probably give up. The original idea was to give an older laptop a new lease of life to be used by my kids but it seems that linux is not quite the answer to everything as I had hoped.

Still I can still use it as an internet pc

Thanks again

---

### Post by deeppurple on 2007-03-03
I have tried to load kplayer but I cant find a package source that works with ap-get..

does anyone know of a up to data location I can put in source.list that works with ubunut

Thanks

---

### Post by Erlander on 2007-03-04
Hi,  I'm no help on kplayer but am wondering about your problem.

In my mind the question is whether it is a xine problem or a video drivers problem.

So, can you play any videos from other sources.  eg from the internet or can you play DVD's?

To re-install xine in Synapatic Open Synapatic, click on search, enter xine.

It will probably bring up kaffiene and kaffiene-xine.  Right click the green square next to them and select "Mark for Re-installation"

I'm fairly new too, but I hope this helps.

Rob

---

### Post by deeppurple on 2007-03-04
Thanks for all your help everyone but I think I reached the point of no return.

I tried the last suggestion of reloading Xine and Kaffeine and that made no difference.

I still have not found out how to load kplayer in ubuntu so thats no good either.

I really had hope that Ubuntu would have been the answer to my problems but it looks like its not quite as good as I thought.

Thanks to everyone.. you never know I might pick it up later on but now it will just be used as another internet pc for the kids

---

### Post by panch0 on 2007-03-05
On the [home page of KPlayer]("http://kplayer.sourceforge.net/") it has a link to the Kubuntu package, and also has instructions on how to add a repository to the sources.list. So you may try either way.

---

