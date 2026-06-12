---
title: "How To Stream Video To Your iPhone The Easy Way"
date: 2010-04-17
forum: Multimedia Software
---

### Post by rotox on 2010-04-17
Using your wireless network, you can stream video and convert it on the fly by using the AirVideo iPhone app and server from *In Method*. I have installed and tested it using the following software. It's really straight forward so have a go! [U]

Software Used:[/U]
Ubuntu 9.10
wine-1.1.31
Java for Windows 7/XP/Vista/2000/2008/Offline ([http://javadl.sun.com/webapps/download/AutoDL?BundleId=39494](http://javadl.sun.com/webapps/download/AutoDL?BundleId=39494))
AirVideo (Apple iTunes)
AirVideo Server for Windows ([http://www.inmethod.com/air-video/download/Setup225.exe](http://www.inmethod.com/air-video/download/Setup225.exe))
Firestarter


_Instructions_

1. If you haven't installed wine then do so

```
# sudo apt-get install wine
```and then run

```
# winecfg
```to create a WinXP default application set.

2. Java - Download and install the full install win32 version of Java.

```
# wget http://javadl.sun.com/webapps/download/AutoDL?BundleId=39494 -O java-winxp.exe
```( the "-O java-winxp.exe" saves the download as "java-winxp.exe" - I had a huge long file name when I downloaded the file).

Once the download is complete, run the setup

```
#wine ./java-winxp.exe
```The GUI installer will run, just "Next" it until it completes. It will tell you that it can't run the "Windows Java Virtual Machine" - just ignore it.

3. Download and install InMethod's AirVideo server

```
#wget http://www.inmethod.com/air-video/download/Setup225.exe

#wine ./Setup225.exe
```The AirVideo server GUI installer will run, again just "Next" it until it completes.

Now go to "Applications" - "Wine" - "Programs" - "AirVideo Server" - "AirVideo Server".
The AirVideo properties window will appear, and you just need to add your video directories using the "Add Disk Folder" button.

4. Firestarter - Open Firestarter ("System" - "Administration" - "Firestarter").

Click on the Policy tab, and add a new "Inbound traffic policy" by clicking on the green "Plus" symbol.

In the new window "Add new inbound rule", click in the "Port" text box and enter "45631" (without the quotes).

5. Fire up the "App Store" on your iPhone and install AirVideoFree (It is a limited version by as it's free you can test it - I've bought the full version AUD3.99).

Once installed, open AirVideo and click on "Servers". Click on the "Plus" symbol and then "Specify Address Manually". In the "Location" text box enter your computers name or Fixed IP Address, and hit "Save".

Your computer should now be listed under the Servers window. Click on the tab and it will display all of the shared directories that you previously set up on the AirVideo Server. Browse through your video collection and enjoy!

Jason

---

### Post by foleyfresh on 2010-06-02
Just had to say, thank you so much. This app is amazing and the fact that I now have the server running on my Ubuntu server is completely flipping brilliant!

---

### Post by thinktyler on 2010-06-08
Thanks, works with the iPad too!

---

### Post by Bruxxx on 2010-06-14
> **rotox said:**
> text...

I cant get it to work with my Ubuntu server.
I have installed wine but I get this problem when I am going to install Java and Air video.

Problem "Application tried to create a window, but no driver could be loaded."

Please help.

---

### Post by rotox on 2010-06-14
@foleyfresh && @thinktyler: Glad that this was of help for you both!

@Bruxxx: Just a few things to check...

Are you running wine via ssh? If ssh use the following to allow X forwarding

```

ssh -X
```Are you running wine from inside a GUI Desktop? You can't create the AirVideo Server window from a command line login.

Are you running wine at the server? If so run the following it should return ":0.0" or similar

```
echo ${DISPLAY}
```Are you running as root? If so DON'T. Never run wine as root as you can easily have your entire system trashed.

The following code will remove wine from your system (including the wine hidden folder in your home directory)

WARNING this will affect all wine installed applications

```

$sudo apt-get purge wine
$sudo rm ~/.wine
```Now reinstall wine

```

$sudo apt-get install wine
$winecfg
```This should display the winecfg window - if it does then wine is now creating windows.

Follow the first post again and test.

Hope this helps,

J

---

### Post by Bruxxx on 2010-06-15
> **rotox said:**
> 
Text

J


Im running with command line.
Can I get it to work in any way? Without reinstalling.

EDIT: [SOLVED] I installed ubuntu desktop and its working now. 

Thank you for everything rotox!

EDIT 2: [NOT SOLVED] I cant find my server on my iPhone :(
But it's installed on the computer.

---

### Post by rotox on 2010-06-15
Hi Bruxxx,

I'm glad that you've got things almost working.

The only thing that you need to do now is make sure the AirVideo Server is always running - so that means logging in to the Gnome desktop and running AirVideo Server which you can do automatically like this.

Now go to "System" - "Preferences" - "Startup Applications"

Click on "Add" and then "Browse" to...

```

/home/<USERNAME>/.wine/drive_c/Program Files/AirVideoServer/AirVideoServer.exe"
```

Enter "AirVideo Server" in the "Name" box, and then "OK'.

You will need to Log Out / Log In and AirVideo Server will now be running - a small window (the Wine System Tray) will appear with a blue icon that looks like a piece of movie film. Your AirVideo Server is now running.

If you haven't configured it or you want to check the settings then double-click on the icon and the AirVideo Server window will appear. [More info about this in the first post.]

Hope that this helps.

J

---

### Post by kroem on 2010-08-07
Is there any way of tweeking AirServers encoding and streaming performance? It looks as if (from Conky) ffmpeg is only encoding in chunks, and no steady flow, same with my "upload rate".

Would appriciate any help... as it is now converting semi-high bandwidth (~480p) movies wont work, it stops every minute or so.

---

### Post by rotox on 2010-08-08
Hi Kroem,

Sorry but I don't have any info that I can give you to help you tweak AirServer.

However, after a quick search on Google I found that there is a Linux version! I'm happy with running it using wine at the mo as I have no problems even with 720p.

Follow the instructions here
[http://wiki.birth-online.de/know-how/hardware/apple-iphone/airvideo-server-linux](http://wiki.birth-online.de/know-how/hardware/apple-iphone/airvideo-server-linux)

Here is the official forum
[http://www.inmethod.com/forum/posts/list/34.page](http://www.inmethod.com/forum/posts/list/34.page)

It looks as though some people have issues with the Linux version too though.

Good luck and please let everyone know how it works out for you.

Thanks

J

---

### Post by kroem on 2010-08-08
Actually I tried the Linux version, but liked the wine instructions (yours ;) ) more.

It's so weird... when I choose to convert movie in the queue the CPU loads up nicely and converts quick, but it still need to be encoded when watching on a cellular line, even thou I did encode it previously :(

Edit. THank you for a great instruction btw :)

---

### Post by PartisanEntity on 2010-08-08
Hey guys, as you may know, you can install vlc4iphone (now known as OpenStreamer") on the iPhone. This eliminates the need to convert formats, since vlc can play just about any format.

I am wondering if anyone has found a good media streaming server that plays nice with vlc4iphone?

I have minidlna installed on my Ubuntu machine, which works great with my Samsung TV, but I cannot get vlc4iphone to display content from it, mainly because if I point vlc4iphone at my-ip:8200 (the url my ubuntu machine that's running minidlna) then nothing really happens.

---

### Post by rotox on 2010-08-09
@Kroem - You're welcome.

[COLOR=Black]@PartisanEntity - [/COLOR]I haven't heard of minidlna I'll have to take a look at it.

---

### Post by q8_legend on 2010-08-10
I tried "Air Video" on my ubuntu under wine... and it works but I faced a problem...
My problem is that the "Air Video" can't see my other HardDrive partitions that are already installed in my computer, which ubuntu already see them... 

"Air Video" only can see the partition that the wine is installed in it, which is the ubuntu OS partition... How to solve this problem ??

Thanks alot

---

### Post by q8.legend on 2010-08-10
> **q8_legend said:**
> I tried "Air Video" on my ubuntu under wine... and it works but I faced a problem...
My problem is that the "Air Video" can't see my other HardDrive partitions that are already installed in my computer, which ubuntu already see them... 

"Air Video" only can see the partition that the wine is installed in it, which is the ubuntu OS partition... How to solve this problem ??

Thanks alot

Thanks Guys... I solved it ;)

I change the mounted Drive from wine config file ;)

Thanks alot

---

### Post by jodonald on 2010-08-10
Ran through everything no problem but when i try to open air video server it tells me that bonjour isn't installed.  I've looked into installing it but it seems like i did something wrong previously and i can't figure it out.  Any suggestions?

---

### Post by rotox on 2010-08-11
Uninstall AirVideo and then install Bonjour for Windows [http://support.apple.com/kb/DL999](http://support.apple.com/kb/DL999).

Reinstall AirVideo and you should be good to go!

Hope this helps.

J

---

### Post by StrungOut101 on 2010-09-02
Ty

---

### Post by akrivitz on 2011-03-10
i figured this out a few weeks ago and its been working great.

has anyone gotten the remote pin feature working? 

I can only seem to get onto the server when im on my home network.

---

### Post by climber514 on 2011-06-26
I am extremely new to ubuntu (like 2 days old lol).  I have followed the instructions below and where I run into issues is that when I launch Air Video is that it tells me that bonjour isnt installed.  I install the latest one as it instructs and still when I open(Air Video) it tells me that it is still out of date and redirects me back to the apple page to get the latest one  I am not sure how to get around this.

Any help would be awesome!!

Thanks
Phil

---

### Post by mike_tyrell on 2011-10-14
> **climber514 said:**
> I am extremely new to ubuntu (like 2 days old lol).  I have followed the instructions below and where I run into issues is that when I launch Air Video is that it tells me that bonjour isnt installed.  I install the latest one as it instructs and still when I open(Air Video) it tells me that it is still out of date and redirects me back to the apple page to get the latest one  I am not sure how to get around this.

Any help would be awesome!!

Thanks
Phil

try "video stream" in place of air-video it just crashes when u convert video for local copy

---

