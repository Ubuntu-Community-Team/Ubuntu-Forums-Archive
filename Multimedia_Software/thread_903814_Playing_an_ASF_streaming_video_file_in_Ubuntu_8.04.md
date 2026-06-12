---
title: "Playing an ASF streaming video file in Ubuntu 8.04"
date: 2008-08-28
forum: Multimedia Software
---

### Post by shay_ts on 2008-08-28
Hi,

I've tried to watch a lecture in my University site. I could watch it rather well in Windows but in Ubuntu it said an MMS plugin was needed. So I searched at the download manager and installed all the plugins and software containing MMS (like VCL for instance). Then it said I should install ASF plugin, and I've installed the related packages as well.

The situation right now is that I can't see the video although it doesn't specify any error right now - the video is just stuck.

Other videos in other sites work great...

Any ideas?

---

### Post by shay_ts on 2008-08-28
Come on guys... Everyone is replied but me :(

---

### Post by lovinglinux on 2008-08-28
I'm new here, but I would never expect to get a reply after 7 minutes of my first post. Patience is a virtue.

Try this tutorial [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Can you provide the link for testing purposes or is a private area?

---

### Post by shay_ts on 2008-08-28
> **lovinglinux said:**
> I'm new here, but I would never expect to get a reply after 7 minutes of my first post. Patience is a virtue.

Try this tutorial [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Can you provide the link for testing purposes or is a private area?


First of all - thank you. I just saw that all the other posts got replies within seconds.

Second of all, you sent me to a long guide which I tried to follow but got too tired to keep up with all the information in it... All I want is a specific solution to a specific problem...

I hope that does not sound rude, I truly appreciate your help. I just don't have time to read all the manuals in order to install one codec which I must have until tomorrow (afterwards I shall read it all and I thank you for that).

S.

---

### Post by shay_ts on 2008-08-28
> **lovinglinux said:**
> 

Can you provide the link for testing purposes or is a private area?

Unfortunately, it is a private area.

---

### Post by lovinglinux on 2008-08-28
> **shay_ts said:**
> First of all - thank you. I just saw that all the other posts got replies within seconds.

Second of all, you sent me to a long guide which I tried to follow but got too tired to keep up with all the information in it... All I want is a specific solution to a specific problem...

I hope that does not sound rude, I truly appreciate your help. I just don't have time to read all the manuals in order to install one codec which I must have until tomorrow (afterwards I shall read it all and I thank you for that).

S.

OK, this are simplified steps from that tutorial to install Gecko Media player and plugins for QuickTime, RealPlayer and Windows Media streams, assuming you are on a **32-Bit Ubuntu 8.04** and using Firefox. I really don't know if it will work, because I never watched an ASF streaming with it, but I think it should handle them.

> Open the terminal (Applications > Accessories > Terminal) and paste these wget commands into it:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update.

```



I don't know if it is really necessary to uninstall all other plugins in order to allow Gecko Media player, since it is possible to disable plugins within Firefox. Nevertheless, the command for removing other media plugins is below:

```
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
```

Now to install the Gecko Media Player

```
sudo apt-get install gnome-mplayer gecko-mediaplayer
```

This could work, but I strongly suggest that you read that tutorial entirely. If you encounter any plugin issues (specially Quicktime related) that weren't present before the installatyion of Gecko Media Player then refer to the Troubleshooting section of the original tutorial.

---

### Post by shay_ts on 2008-08-28
After I enter the window in which the movie is supposed to be shown, I see a gray big box and nothing happens. After I click this gray box, an error window of the movie player appears, and it says the following:

"An error occurred 
The playback of this movie requires the following decoders which are not installed:

Windows media video 9 decoder
Windows Media video 9 decoder
Windows Media Audio 8 decoder
Windows Media Audio 8 decoder
windows media video 9 decoder
windows media audio 8 decoder"

Needless to say that I've done everything that you've said.

I also have a greasemonkey installed, if that is important.

I read the troubleshooting guide - and couldn't find the answer. I should say again that it's probably NOT a quicktime player problem, but I'm rather a moron in matters of linux so every tip will be welcomed.

Once again, I appreciate the support.

---

### Post by shay_ts on 2008-08-28
Farthermore, you can press on the following links and see whether YOU can play this format: 

[http://www.openu.ac.il/Events/210605.html](http://www.openu.ac.il/Events/210605.html)

---

### Post by lovinglinux on 2008-08-28
I'm a Linux moron too.

I did a search for "Windows media video 9 decoder" and found this:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

One thing you should consider if anyone else post a solution or if you can't find it using searching the forums is to contact the University webmaster to know if the site support Linux. 

I have similar problem related to the website support. My ISP provider makes me pay for an extra "content provider" which only perform the network authentication (this is currently under legal dispute in my country). Anyway, the "content provider" has a video streaming service with movies and TV shows like "Desperate Housewives", "Criminal Minds", "Lost" and "Grey's Anatomy", but I can't watch them under Linux because the provider has an evil contract with Microsoft. So they do not support Linux users. This really pisses me off now that I'm a Linux user and completely wiped Windows from my computer.

---

### Post by shay_ts on 2008-08-28
The site DOES NOT support linux. However, I am trying to find a way of downloading the asx file of the movie.

Do you know how can I download an ASX file?

---

### Post by lovinglinux on 2008-08-28
> **shay_ts said:**
> The site DOES NOT support linux. However, I am trying to find a way of downloading the asx file of the movie.

Do you know how can I download an ASX file?

ASX or ASF? 

If you are using Firefox, try "[Download Helper]("http://www.downloadhelper.net/")" extension. It has support for ASF files. After installing the extension right click in the Firefox toolbar and slect customize, then add the "Download Helper" icon to the toolbar.Go to the video web site. If the extension can capture the video, it will blink and you would be able to see a list of available files for download when clicking over it.

---

### Post by shay_ts on 2008-08-28
I succeeded downloading the asx but the guys there made it the asx file of the portal instead of the movie.. errg

---

### Post by lovinglinux on 2008-08-28
> **shay_ts said:**
> I succeeded downloading the asx but the guys there made it the asx file of the portal instead of the movie.. errg

Did you downloaded with "Download Helper"? If yes, look for other files in the download list before downloading. Maybe it will be there.

While I was searching for a solution to your problem I discovered that the TV site I mentioned in the previous post is working now with Gecko Mediaplayer. w00t!

---

### Post by wolfen69 on 2008-08-28
for a streaming .asf file i just right click the link>copy link address. then open vlc>file>open network stream>http and paste address. hit OK. it works most of the time, and not for only .asf, but for other things like apple movie trailers.

---

### Post by shay_ts on 2008-08-29
> **wolfen69 said:**
> for a streaming .asf file i just right click the link>copy link address. then open vlc>file>open network stream>http and paste address. hit OK. it works most of the time, and not for only .asf, but for other things like apple movie trailers.


Somebody told me to install the new Beta version of vlc... I've downloaded the file but have got no idea how to install it... 
Can you guide me?

Thank you!!! :)

---

### Post by shay_ts on 2008-08-29
> **wolfen69 said:**
> for a streaming .asf file i just right click the link>copy link address. then open vlc>file>open network stream>http and paste address. hit OK. it works most of the time, and not for only .asf, but for other things like apple movie trailers.


And... The solution offered does not work, unfortunately. Perhaps that is because the user must log in using password in order the movie will be presented in the explorer window (in windows)

---

### Post by greyspoke on 2008-10-19
I have had streaming problems with Windows media (I posted on that helpful media tutorial thread also).  Various media players play the files fine from disc (I have access to them).  But they won't play the stream at all/ at all well.  VLC does OK playing the stream directly (telling it to play the .wmv file directly with the mms protocol) but with no control - you can't pause it, only stop completely.  But it's plug-in doesn't work at all.  Others don't work any way, though again they play the raw file just fine.  The media are on a Helix server and the links in the web pages are to the .wmv files using the /asxgen/ logical folder to generate the asx files.  (Don't press me on this, that is about as much as I know about streaming media, and it doesn't appear to be sufficient).

It definitely appears to be a problem with streaming rather than codecs etc.

---

### Post by Khrissi on 2009-01-12
> **lovinglinux said:**
> OK, this are simplified steps from that tutorial to install Gecko Media player and plugins for QuickTime, RealPlayer and Windows Media streams, assuming you are on a **32-Bit Ubuntu 8.04** and using Firefox. I really don't know if it will work, because I never watched an ASF streaming with it, but I think it should handle them.



I don't know if it is really necessary to uninstall all other plugins in order to allow Gecko Media player, since it is possible to disable plugins within Firefox. Nevertheless, the command for removing other media plugins is below:

```
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
```

Now to install the Gecko Media Player

```
sudo apt-get install gnome-mplayer gecko-mediaplayer
```

This could work, but I strongly suggest that you read that tutorial entirely. If you encounter any plugin issues (specially Quicktime related) that weren't present before the installatyion of Gecko Media Player then refer to the Troubleshooting section of the original tutorial.

:KS Good one ! Got my .asf files running on Elonex webbook-relly easily ( check sound config Tho!) Ubuntu 8.1 xx

---

