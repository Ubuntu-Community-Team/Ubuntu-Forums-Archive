---
title: "Unable to view videos in crunchyroll.com"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by ahfu on 2007-12-25
Hi there!

I am a newbie to linux and I am currently using Ubuntu v7.10...

I am currently also unable to view videos in crunchyroll.com, however i am able to view videos in youtube,com

I had done the followings

sudo apt-get install ubuntu-restricted-extras and also follow the instructions in
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

but still could not view videos in crunchyroll..

As I am a newbie in linux, I would really appreciate if you could reply in a way that newbies like me can understand. Thanks!

Ah Fu

---

### Post by ubuntu27 on 2007-12-25
Hello there. Before we could help you, I have some questions for you. 
Are you using UBuntu, Kubuntu, or Xubuntu?

ALso, did you install Flash Player (and which one?  Adobe's Flash or also known as 'non-free flash'
or GNASH ? )

[RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")


Either case, open the terminal  [Applications menu/Accessories/Terminal]

and type the following (you can copy & paste)

```
sudo apt-get install flashplugin-nonfree
```


[Follow this link for how-to install Flash with screenshots]("http://www.psychocats.net/ubuntu/flash")

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by ahfu on 2007-12-25
> **ubuntu27 said:**
> Hello there. Before we could help you, I have some questions for you. 
Are you using UBuntu, Kubuntu, or Xubuntu?

ALso, did you install Flash Player (and which one?  Adobe's Flash or also known as 'non-free flash'
or GNASH ? )

[RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")


Either case, open the terminal  [Applications menu/Accessories/Terminal]

and type the following (you can copy & paste)

```
sudo apt-get install flashplugin-nonfree
```


[Follow this link for how-to install Flash with screenshots]("http://www.psychocats.net/ubuntu/flash")

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Hi,

Thanks for the reply! I guess I should be using Ubuntu and GNOME as there exists System > About GNOME and System > About Ubuntu.

My version of GNOME is 2.20.1
My version of Ubuntu is 7.10

Also, when I tried "]sudo apt-get install flashplugin-nonfree", 
i get "flashplugin-nonfree is already the newest version. So, i supposed I had already installed "flashplugin-nonfree".

Any idea what I should do next to make crunchyroll.com work? Thanks.


Anyway, may I ask is UBuntu, Kubuntu, or Xubuntu somehow related? Also, what is the difference between GNOME and KDE? Pls do not give too technical replies as I dun think I will be able to understand anyway. Hehe.. 


Ah Fu

---

### Post by ubuntu27 on 2007-12-25
Ubuntu 7.10.   ok. ANd what browser are you using? (epihany, firefox, opera, etc) ?

It seems strange to me that you can see youtube's videos and not crunchyroll.

When you log in to Crunchyroll and play a video. do you hear any sound?  Just recently CrunchyROll has change its video player in order ot be able to use the latest Flash Player ability to handle H.264 (a high definition video). Maybe the problems rest there.


ok do the following:

1) OPen Synaptic Package Manager from   System/Administration/ Synaptic

2) look for flashplugin-nonfree  and tell me what version it is.

3) Look for gnash, and see if it is installed. (it should not be installed)

4) tell me the browser that you are using and its version

Also, just in case:
**From Medibuntu**

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install w32codecs
```



***************

GNOME, KDE, XFCE, etc are Desktop environment (DE)

[http://en.wikipedia.org/wiki/Desktop_environment]("http://en.wikipedia.org/wiki/Desktop_environment")

---

### Post by ahfu on 2007-12-25
Hi,

I am now using Firefox. Help > About Mozilla Firefox gives the following.
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

My flashplugin-nonfree is version 9.0.48.0.2+really0ubuntu12.

Yes, I checked and I have gnash installed, I have uninstalled it since you told me to do so.

With gnash installed - i can hear sounds but no video in crunchyroll.com
With gnash uninstalled - I cannot hear sounds nor see video in crunchyroll.com
However, with or without gnash, i can watch video normally in youtube.com

I also did the following four commands and they completed with success.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install w32codecs
```

So, to summarise, the current status is that I can still watch videos on youtube normally. And on crunchyroll, i hear no sound (after I uninstall gnash) and see no video. 

sidenote: I learn quite abit from your ubuntu guide links. Thanks!


Ah Fu

---

### Post by ubuntu27 on 2007-12-29
> **ahfu said:**
> Hi,

I am now using Firefox. Help > About Mozilla Firefox gives the following.
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

My flashplugin-nonfree is version 9.0.48.0.2+really0ubuntu12.



**With gnash installed - i can hear sounds but no video in crunchyroll.com**
With gnash uninstalled - I cannot hear sounds nor see video in crunchyroll.com
However, with or without gnash, i can watch video normally in youtube.com
[
So, to summarize, the current status is that I can still watch videos on youtube normally. And on crunchyroll, i hear no sound (after I uninstall gnash) and see no video. 

sidenote: I learn quite a bit from your ubuntu guide links. Thanks!


Ah Fu

I been lurking around [CruchyRoll's Forum]("http://www.crunchyroll.com/forum"). It seems that those who have the same symptom are BOTH WIndows Users and GNU/Linux users. It seems to be a bug in Adobe's Player. Shinji, one of the Site creator said that He has added a bugreport link for those with audio but no video."

So try clicking on "having problems? try the old player" Link that appears below a video.

Do you have a star account? If you don't have one, tell me your UserName in that site (you can PM me on that) so I could give you a star if you want [a Christmas Present from me!!] :popcorn:

Also, I don't think that it would solve your problem but, try installing the "flashplayer-mozilla" package. (it will replace flashplugin-nonfree. Say yes when asked to confirm action) 
If it still didn't work, install  flashplugin-nonfree again.

---

### Post by kiko0850 on 2008-01-30
Woops posted twice the method on how i fixed it is on the bottom post

---

### Post by kiko0850 on 2008-01-30
I had the same problem, i had the problem that it would play but it was in like a weird way, but i was able to figure out how to fix the problem.  Here is what i did:

1. uninstall gnash and flashnonfree
2. restart computer
3. install flashnonfree
4. go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")
5. download the tar file and also follow the instructions in installing it
6. restart your computer

and it worked for me, i used this with the standard ubuntu not the 64 amd version, so not sure if that will work for you

Hopefully this helps!!

Cheers,
kiko

---

### Post by ubuntu27 on 2008-01-31
> **kiko0850 said:**
> I had the same problem, i had the problem that it would play but it was in like a weird way, but i was able to figure out how to fix the problem.  Here is what i did:

1. uninstall gnash and flashnonfree
2. restart computer
3. install flashnonfree
4. go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")
5. download the tar file and also follow the instructions in installing it
6. restart your computer

and it worked for me, i used this with the standard ubuntu not the 64 amd version, so not sure if that will work for you

Hopefully this helps!!

Cheers,
kiko

Thank you Kiko. The problem was in the Flash player itself then. THe Flash player in the repository is an old version. Download and install Flash from adobe.com

Also, note that Flash is still buggy. People who use browser other than firefox has problems. See "[Why Flash Sucks"]("http://www.kdedevelopers.org/node/3162") by a KDE developer.
Hope Adobe fix all those problems soon.

[http://www.kdedevelopers.org/node/3162](http://www.kdedevelopers.org/node/3162)

---

