---
title: "Mythbuntu 9.10 - setup no external channel changer option"
date: 2010-02-06
forum: Mythbuntu
---

### Post by tamalotes on 2010-02-06
I have enabled to use a RF-Blaster via UART for my Motorola STB.
However, when I enter the configuration screen (Connect source input) --> [http://www.mythtv.org/wiki/File:Setupconnection.jpg](http://www.mythtv.org/wiki/File:Setupconnection.jpg)  there is no option to setup the script nor a preset channel.

I have found a similar issue --> [http://ubuntuforums.org/showthread.php?t=1229001](http://ubuntuforums.org/showthread.php?t=1229001) 
But seems like that post is dead...

Any help will be appreciated.

Regards,
-Carlos

---

### Post by srmcatee on 2010-02-08
Do you have a video source selected?

You need to create the channel change script yourself.  Here is an example of one you can download.

[http://www.commandir.com/component/option,com_jdownloads/Itemid,53/task,view.download/cid,4/](http://www.commandir.com/component/option,com_jdownloads/Itemid,53/task,view.download/cid,4/)

Also, the channels and preset will show up once you have a video source created and selected.

---

### Post by tamalotes on 2010-02-08
Thanks Srmcatee - But I do have a video-source selected.
If I unselect my video source, the "scan for channels" and "fetch channels" get grayed-out.

BTW - the fetch channels from list source, does not work either.
I have a post describing that issue as well --> [http://ubuntuforums.org/showthread.php?t=1400317](http://ubuntuforums.org/showthread.php?t=1400317)

Thanks,
-CGS

******
BTW - I have setup a script channel changer in the past. So I already have a script.

---

### Post by sachag on 2010-02-08
Hi, 

You can change/set the channel change script directly in the Database. 

It's a part of my wiki entry about the integration of dreamboxes:

[http://www.mythtv.org/wiki/Dreambox-NetworkRecorder#The_channel_change_script](http://www.mythtv.org/wiki/Dreambox-NetworkRecorder#The_channel_change_script)

regards

Sacha

---

### Post by ian dobson on 2010-02-08
Hi Sacha,

Looks interesting, I have a dbox clone running a neutrino image. How do you handel EPG? Do you need to use an external XMTV grabber?


tamalotes sorry for sidetracking your thread.

Regards
Ian Dobson

---

### Post by tamalotes on 2010-02-08
As I keep digging this issue, it seems like Digital tuners do not support external STB (or use of a script to change channels)
 
[http://svn.mythtv.org/trac/ticket/1422](http://svn.mythtv.org/trac/ticket/1422)
 
With that said, does anybody know what the limitation is? It is just the lack of an I/F to add the script, so the suggestion from sachag:
 
>  
It's a part of my wiki entry about the integration of dreamboxes:

[[COLOR=#000000]http://www.mythtv.org/wiki/Dreambox-..._change_script[/COLOR]]("http://www.mythtv.org/wiki/Dreambox-NetworkRecorder#The_channel_change_script")

regards


 
will actually work, or there are other limitations into this configuration...
 
Bottom line: What will be the easiest way to support HD from a STB?
 
-CGS

---

### Post by azmyth on 2010-02-08
My guess would be you've setup the tuner as a us-broadcast or you scanned or set as ATSC thus myth thinks you're using the tuner for over the air (OTA) and having a change channel script wouldn't make sense.

---

### Post by nickrout on 2010-02-08
> **tamalotes said:**
> As I keep digging this issue, it seems like Digital tuners do not support external STB (or use of a script to change channels)
 
[http://svn.mythtv.org/trac/ticket/1422](http://svn.mythtv.org/trac/ticket/1422)
 
With that said, does anybody know what the limitation is? It is just the lack of an I/F to add the script, so the suggestion from sachag:
 

 
will actually work, or there are other limitations into this configuration...
 
Bottom line: What will be the easiest way to support HD from a STB?
 
-CGS

You can't use a digital tuner with an STB, an STB outputs an analogue TV picture. You need an analogue tuner.

What's more to get the HD output from a STB you will need to use an HDPVR and plug the component cables (thats three of them plus audio) into it.

---

### Post by sachag on 2010-02-09
Hi Ian,

thx. Yes i use an external XMLTV Grabber. When i have a bit more time, i try to get EPG data from the dreambox as well. A mix will be fine. Right now i don't now how to export the EGP from the dreambox in XMLTV format. Any hints ?

regards

Sacha

> **ian dobson said:**
> Hi Sacha,

Looks interesting, I have a dbox clone running a neutrino image. How do you handel EPG? Do you need to use an external XMTV grabber?


tamalotes sorry for sidetracking your thread.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-02-09
Hi,

You'll need to write a http screen scraper. Basicly a script that grabs a web page with the epg text, splits off the epg data and writes it to an xml file. Not an easy job. I might have a go at writing something if I get the streaming part working.

The script would only work for a dbox running a neutrino image.

I've got my dbox so far that I can stream a TV channel to my winodws PC running VLC, but I need to manually select the correct channel using the remote/web frontend before I card VLC. I've had a look at the web page but can't seem to find the cgi script that actually does the channel changing. It appears to be built into the neutrino executable.

I take it your in switzerland based on the channel list in the wiki entry.

Regards
Ian Dobson

---

### Post by nickrout on 2010-02-09
surely there is an xmltv grabber for Switzerland? tv_grab_ch_search seems to be for Switzerland, although whether it works is not for me to say, as I don't live there.

---

### Post by ian dobson on 2010-02-10
Hi,

I've used tv_grab_ch_search works but it has some "problems":-

1) They don't have all the channels I need
2) It's really slow
3) Wastes network bandwidth (I have all the data on the dbox)

But this is a different story/for a different thread.

Regards
Ian Dobson

---

### Post by sachag on 2010-02-12
> **nickrout said:**
> You can't use a digital tuner with an STB, an STB outputs an analogue TV picture. You need an analogue tuner.

What's more to get the HD output from a STB you will need to use an HDPVR and plug the component cables (thats three of them plus audio) into it.

Wrong. As i wrote on my wikipage, i stream every channel directly from the STB (Dreamboxes) to MythTV including the HD channels.

Sacha

---

### Post by nickrout on 2010-02-12
but this thread is not about dreamboxes

---

