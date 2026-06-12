---
title: "PS3 Media Server Configuration via Command Line"
date: 2010-03-04
forum: Multimedia Software
---

### Post by endlessracingz on 2010-03-04
Before people post giving me a list of all my options for an DLNA, upnp, and media servers I've gone through ushare, then wanted transcoding for my mkv files so i went to fuppes. Fuppes failed me and I could not find help for my specific problem not even on these forums. So now I'm on to PS3 Media Server. I have thought about using mediatomb but after installing PS3 Media Server on my Ubuntu 9.1 Server everything worked instantly. My mkv files played instantly an well.

However, there is a lack of documentation and what there is out there as far as documentation is concerned all involves having a GUI... well I am usuing ubuntu server and therefore have no gui. I haven't been able to find a way to configure it through the command line as of yet.

So any help on this would be greatly appreciated!

---

### Post by pcit on 2011-01-13
I'd like to bump this post as I have exactly the same question.

Hopefully there is a way around it after 8 months :P

---

### Post by PlaidRadish on 2011-08-19
Bump!

I am running Ubuntu Server, as well...strange that more people have not requested help on this?

-jeff

---

### Post by xelasha on 2011-09-26
For a few basic configurations

>  ~/.config/PMS/PMS.conf

For rendering configurations, they are located in the PS3 Media Server directory under the folder "renderers". 

Unfortunately the PMS.conf is fairly limited with only five lines of options. 

> thumbnails = true
mecoder-*** = true
folders = [preferable directory here]
uuid = [generated]
image_thumbnails = true

Hope this helps!

---

### Post by BDStudio on 2011-11-03
I have configured Server 10.04 with PS3 media server 1.40.0 via command line and It is working. I used the guide form irrationale as groundwork to get it working but it took alot of research since I did not want to use gui. Here is the link for the guide I used: [http://irrationale.com/2010/06/30/ps3-media-server-on-ubuntu-10-04/](http://irrationale.com/2010/06/30/ps3-media-server-on-ubuntu-10-04/)
 As far as the PMS.conf only having 5 configurable parameters that is what I have found with alot of guides I found but in all honestly it has more. I found this out by installing PS3 media server on Desktop 10.04 and configuring all the parameters I wanted. Then I opened the PMS.conf file to find the code I needed to use for my server. Alot of what I did was trial and error but I have a basic PS3 media server up and running without running a gui of any sort. If you want me to post a guide on how I did it let me know. I don't have a digital copy of the guide yet but I have it down on paper.

---

### Post by BDStudio on 2011-11-03
[FONT=Cambria][SIZE=7][COLOR=#17365d]Installing PS3 Media Server on Ubuntu Server 10.04 LTS via command line[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman]I have seen a lot of people looking for a command line guide to install PS3 Media Server on Ubuntu. I was also looking for a guide myself and found a few that I used for the groundwork. All of the guides I found used a GUI for some portion of the configuration but I wanted strictly command line since I do not have any GUI on my server. After alot of searching and trial and error I finally got it up and running. The main sources I used were [Socrateos]("http://socrateos.blogspot.com/2011/01/1.html"), [Irrationale]("http://irrationale.com/2010/06/30/ps3-media-server-on-ubuntu-10-04/"), and [Ubuntu Community Documentation]("http://help.ubuntu.com/community/Ps3MediaServer"). Here is how I configured my server. I have tested this on both 32 bit and 64 bit systems.[/FONT]
**[FONT=Cambria][SIZE=5][COLOR=#365f91]Step 1: Install the pre-requisites.[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri][SIZE=3]Code:[/SIZE][/FONT]
[FONT=Calibri]sudo apt-get install mencoder ffmpeg mplayer vlc openjdk-6-jre [/FONT]

[FONT=Calibri]I had to install MediaInfo since my server gave a libmediainfo not found error when I started PS3 Media Server. [/FONT]
[FONT=Calibri]**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Install MediaInfo[/COLOR][/SIZE][/FONT] **
 
**[COLOR=#4f81bd][FONT=Cambria][SIZE=3]Add Python-Software Properties[/SIZE][/FONT][/COLOR]**
 
Code:
[FONT=Calibri]sudo apt-get install python-software-properties[/FONT]
[FONT=Calibri]**[FONT=Cambria][SIZE=3][COLOR=#4f81bd]Add the repository and install MediaInfo[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri]Code:[/FONT]
[/FONT][/FONT][FONT=Calibri]sudo apt-add-repository ppa:shiki/mediainfo[/FONT]
[FONT=Calibri]sudo apt-get update[/FONT]
[FONT=Calibri]sudo apt-get install mediainfo[/FONT]
 
[FONT=Calibri]**[FONT=Cambria][SIZE=5][COLOR=#365f91]Step 2: Download and unpack PS3 Media Server[/COLOR][/SIZE][/FONT]**
 
 
**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Download PS3 Media Server into your home directory.[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri][FONT=Calibri]Code:[/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][FONT=Calibri]sudo wget [http://ps3mediaserver.googlecode.com/files/pms-generic-linux-unix-1.40.0.tgz](http://ps3mediaserver.googlecode.com/files/pms-generic-linux-unix-1.40.0.tgz)[/FONT][/FONT][/FONT]

[FONT=Calibri][FONT=Calibri][FONT=Calibri]**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Unpack PS3 Media Server[/COLOR][/SIZE][/FONT]**
 
Code:
[/FONT][/FONT][/FONT][FONT=Calibri][FONT=Calibri][FONT=Calibri]sudo tar xzf pms-generic-linux-unix-1.40.0.tgz[/FONT][/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][FONT=Calibri]**[FONT=Cambria][SIZE=5][COLOR=#365f91]Step 3: Move PS3 Media Server to the opt folder and give it rights to run.[/COLOR][/SIZE][/FONT]**
 
 
**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Move PS3 Media Server[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri]Code:[/FONT]
[FONT=Calibri][FONT=Calibri]sudo mv ~/pms-linux-1.40.0 /opt/pms[/FONT][/FONT]
[FONT=Calibri][FONT=Calibri]**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Give PS3 Media Server rights to run.[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri]Code:[/FONT]
[FONT=Calibri]cd /opt/pms[/FONT]
[FONT=Calibri]sudo chmod +x PMS.sh[/FONT]
[FONT=Calibri]sudo chmod +x linux/tsMuxeR[/FONT]
[FONT=Calibri]**[FONT=Cambria][SIZE=5][COLOR=#365f91]Step 4: Modify the config file.[/COLOR][/SIZE][/FONT]**
 
On both systems I tested this on there was no config file until I started PS3 Media Server. The only thing it generated was the uuid. If you want to start it and then modify the config file use this code:
sudo ./PMS.sh
Once it comes up it will look like it has locked up and your unable to type anything. Just hit Ctrl +x to shut it back down and then modify the config file.
**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Open the config file.[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri]Code:[/FONT]
[FONT=Calibri][FONT=Calibri]sudo nano PMS.conf[/FONT][/FONT]

[FONT=Calibri][FONT=Calibri]This is how I set up my config file. I am not exactly sure what all the code does but I will try to explain what I can.[/FONT]
[FONT=Calibri][FONT=Calibri]In the config file:[/FONT]
[FONT=Calibri]thumbnails = true *[FONT=Calibri]enables thumbnails[/FONT]*
image_thumbnails = true *[FONT=Calibri]enables image thumbnails[/FONT]*
uuid = [*generated*] *[FONT=Calibri]uuid computer generates[/FONT]*
network_interface = eth0 *[FONT=Calibri]ties PMS to an interface[/FONT] *
hidevideosettings = true [FONT=Calibri]*hides video settings*[/FONT]
hide_transcode_folder = true [FONT=Calibri]*hides #transcode# folder*[/FONT]
hide_extensions = true [FONT=Calibri]*hides file extensions*[/FONT]
hide_enginenames = true [FONT=Calibri]*not really sure???*[/FONT]
folders = */path/to/directory, /path/to/directory2* [FONT=Calibri]paths to your media to stream[/FONT]
[FONT=Calibri]Save and close the config file.[/FONT]
[FONT=Calibri]**[FONT=Cambria][SIZE=5][COLOR=#365f91]Step 5: Test PS3 Media Server[/COLOR][/SIZE][/FONT]**
 
 
**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Start PS3 Media Server and check for errors[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri]Code:[/FONT][/FONT]
[FONT=Calibri]sudo ./PMS.sh[/FONT]
[FONT=Calibri]**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Stop PS3 Media Server[/COLOR][/SIZE][/FONT]**
 
Ctrl + X
**[FONT=Cambria][SIZE=5][COLOR=#365f91]Step 6: Make PS3 Media Server start at boot[/COLOR][/SIZE][/FONT]**
 
**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Create a script[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri]Code:[/FONT]
[FONT=Calibri]cd /etc/init.d[/FONT]
[FONT=Calibri][FONT=Calibri]sudo nano startpms[/FONT]

[FONT=Calibri][FONT=Calibri]**Add the following to the script:**[/FONT][/FONT]
[FONT=Calibri][FONT=Calibri]#!/bin/bash[/FONT]
[FONT=Calibri]cd /opt/pms[/FONT]
[FONT=Calibri]nohup ./PMS.sh &[/FONT]
[FONT=Calibri]exit[/FONT]
[FONT=Calibri]**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Save and exit the file and make it executable.[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri]Code:[/FONT]
[FONT=Calibri][FONT=Calibri]sudo chmod +x startpms[/FONT][/FONT]
[FONT=Calibri][FONT=Calibri]**[FONT=Cambria][SIZE=4][COLOR=#4f81bd]Insert the file into startup config[/COLOR][/SIZE][/FONT]**
 
[FONT=Calibri]Code:[/FONT]
[FONT=Calibri][FONT=Calibri]sudo update-rc.d startpms defaults[/FONT][/FONT]

[FONT=Calibri][FONT=Calibri][FONT=Times New Roman]All I did after this point was restart my server and make sure the script worked. My videos showed up and played on my PS3, Xbox 360 and to my surprise my LG Blu-Ray player. I hope this guide helps. I am not guaranteeing this will work on every build but it worked when I tried it on Ubuntu Server 10.04 LTS 32 bit and 64 bit. I did not use a gui and the only things I had running was a Samba server and ssh on a headless server. I am still working on polishing my configuration files for PS3 Media Server since my LG player does not play all my movies and my Xbox 360 sometimes has issues seeing new videos I place in the directory and does not recognize new folders unless I restart the server. If anyone has anything to add or knows how to restart the HTTP part of PS3 Media Server I would be interested in reading your comments.[/FONT]
[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by just_cruising on 2012-02-19
awesome guide, i just tried it and worked without any issues what so ever.

---

### Post by foug on 2012-03-24
i get a "missing libzen" error, any ideas?

---

### Post by melophat on 2012-08-02
> **foug said:**
> i get a "missing libzen" error, any ideas?
go to this page:
[http://www.ubuntuupdates.org/package/core/precise/universe/base/libzen](http://www.ubuntuupdates.org/package/core/precise/universe/base/libzen)

and you will see that libzen is a group and you can manually install the group member packages.. This worked for me when i got the libzen error.  The

---

