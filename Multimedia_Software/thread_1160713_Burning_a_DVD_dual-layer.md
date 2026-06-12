---
title: "Burning a DVD dual-layer ?"
date: 2009-05-15
forum: Multimedia Software
---

### Post by oygle on 2009-05-15
I have a DVD dual layer disc, contents show as:

> 
# ls -alR /media/cdrom1
/media/cdrom1:
total 10
dr-xr-xr-x 4 4294967295 4294967295  136 2008-12-14 02:32 .
drwxr-xr-x 6 root       root       4096 2009-05-16 11:15 ..
dr-xr-xr-x 2 4294967295 4294967295   40 2008-12-14 02:28 AUDIO_TS
dr-xr-xr-x 2 4294967295 4294967295  716 2008-12-14 02:28 VIDEO_TS

/media/cdrom1/AUDIO_TS:
total 4
dr-xr-xr-x 2 4294967295 4294967295  40 2008-12-14 02:28 .
dr-xr-xr-x 4 4294967295 4294967295 136 2008-12-14 02:32 ..

/media/cdrom1/VIDEO_TS:
total 6667616
dr-xr-xr-x 2 4294967295 4294967295        716 2008-12-14 02:28 .
dr-xr-xr-x 4 4294967295 4294967295        136 2008-12-14 02:32 ..
-r--r--r-- 1 4294967295 4294967295      12288 2008-12-14 02:28 VIDEO_TS.BUP
-r--r--r-- 1 4294967295 4294967295      12288 2008-12-14 02:28 VIDEO_TS.IFO
-r--r--r-- 1 4294967295 4294967295      45056 2008-12-14 02:28 VIDEO_TS.VOB
-r--r--r-- 1 4294967295 4294967295      71680 2008-12-14 02:28 VTS_01_0.BUP
-r--r--r-- 1 4294967295 4294967295      71680 2008-12-14 02:28 VTS_01_0.IFO
-r--r--r-- 1 4294967295 4294967295  120315904 2008-12-14 02:28 VTS_01_0.VOB
-r--r--r-- 1 4294967295 4294967295 1073739776 2008-12-14 02:28 VTS_01_1.VOB
-r--r--r-- 1 4294967295 4294967295 1073739776 2008-12-14 02:28 VTS_01_2.VOB
-r--r--r-- 1 4294967295 4294967295 1073739776 2008-12-14 02:28 VTS_01_3.VOB
-r--r--r-- 1 4294967295 4294967295 1073739776 2008-12-14 02:28 VTS_01_4.VOB
-r--r--r-- 1 4294967295 4294967295 1073739776 2008-12-14 02:28 VTS_01_5.VOB
-r--r--r-- 1 4294967295 4294967295 1073739776 2008-12-14 02:28 VTS_01_6.VOB
-r--r--r-- 1 4294967295 4294967295  264667136 2008-12-14 02:28 VTS_01_7.VOB


When I insert it in the DVD player/burner, it shows okay in Ubuntu, using Movie player.

How do I burn this (make a copy) on Jaunty, 64 bit Ubuntu, as dual-layer, so that the DVD burnt is an exact copy of the dvd disc I have at present ?

Thanks,

Oygle

---

### Post by alwayshere on 2009-05-15
k9copy should do the trick use below command to install it. you will find launcher under sound and video.




sudo apt-get install k9copy

---

### Post by oygle on 2009-05-15
Great, thanks.  :)

---

### Post by oygle on 2009-05-16
k9copy did half of the job, it copied from the DVD to a folder. But then an error, can't open the folder /tmp/kde-****/k9copy/ , even though the files are there, and permissions are okay.

Any better tool than k9copy ?

Oygle

PS I should mention that the DVD I'm copying 'from' is also dual-layer disc, and the DVD I'm copying 'to' is a blank dual layer disc. Does the blank disc have to be formatted ?

---

### Post by stilling on 2009-05-16
sudo apt-get install k3b
under the panel where you insert the files that you whant to burn on the program window right click of your mouse and select 8.0 gb or auto ... add your file burn and that is all .

Hope this will help you.

---

### Post by oygle on 2009-05-16
Thanks, I installed k3b , and it's now copying the DVD to an image on disk. Will then try see if it prompts for the empty disc, and see how it goes.

Oygle

---

### Post by oygle on 2009-05-16
K3b rocks.  :popcorn:

Am able to play the copied DVD just fine.

Will uninstall k9copy.  :icon_frown:

---

### Post by stilling on 2009-05-21
you can remove k9copy from synaptic package manager or by typing in terminal 
sudo apt-get remove k9copy 
to completly remove that means the configuration file to
sudo apt-get purge k9copy

hope it helps you

---

### Post by oygle on 2009-05-22
When I used used K3b, it copied the DVD to disc, and an .ISO was created. Then K3b dialog told me all went okay. Then I burnt a DL DVD from the .ISO , using K3b, again the K3b dialog told me all was okay.

Played it with Movie Player, just a few mins, looked okay, then played it on a DVD player. The start was okay, plus various 'titles' played okay. Then played one title, and it was okay, but after about 3 mins of playing, the frame freezes, and stayed frozen for several minutes. No audio, and the video just froze.

I used a Verbatim 8x DVD+R DL disc. Don't want to use another, as it's a waste, but will get a DVD-RW DL or similar, so I can test this some more.

The .ISO is still on disk. Any clues please ?

Oygle

---

### Post by alphacrucis2 on 2009-05-22
To check that the iso file is ok, You could just open the iso file in VLC and see if it plays. That would verify that the first step worked correctly. You might be able to open the iso file from Totem or MPlayer but I am not sure as I have only ever tried that from VLC. By the way I wouldn't be so hasty to get rid of k9copy as it has the useful function of shrinking video files down if you need to go from double layer to single layer which I don't think K3B can do.

---

### Post by solitaire on 2009-05-22
Oygle

Have you used that brand of DVD's in that DVD player before?
I know most DVD players are very picky when it comes to Burned DVD's you might want to try a different brand.

But if you have used that brand beforei nteh DVD and it went OK then it might be a problem with the burning. Check the ISO in VLC then try a diffrent program to burn it to a DVD. See if that makes a diffrence.

---

### Post by oygle on 2009-05-27
> **alphacrucis2 said:**
> To check that the iso file is ok, You could just open the iso file in VLC and see if it plays. That would verify that the first step worked correctly. You might be able to open the iso file from Totem or MPlayer but I am not sure as I have only ever tried that from VLC. By the way I wouldn't be so hasty to get rid of k9copy as it has the useful function of shrinking video files down if you need to go from double layer to single layer which I don't think K3B can do.

I don't know what VLC is, sorry. I am able to open the ISO in archive manager and view the contenst, which look the same as the original DVD. I couldn't open/play the ISO in Movie player though.

Will keep in mind the notes about k9copy also.

Thanks.  :)

---

### Post by oygle on 2009-05-27
> **solitaire said:**
> 
Have you used that brand of DVD's in that DVD player before?


Yes, I matched up the DVD exactly. The original DVD is a verbatim 8x DVD+R DL , and the DVD I burnt 'to', is eactly the same brand and type.

The original DVD I could play okay on the DVD player, the copy I could play, but found a section that just feezes on the same frame for several minutes. That section also plays okay , using the original DVD.

> **solitaire said:**
> 
Check the ISO in VLC then try a diffrent program to burn it to a DVD. See if that makes a diffrence.

Am downloading/installing VLC now. Will buy some DVD+RW DL , so that I don't waste the 'write once' type of discs, this obviously needs a bit of testing.

Thanks,

Oygle

---

