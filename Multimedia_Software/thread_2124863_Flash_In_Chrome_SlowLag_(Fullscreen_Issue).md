---
title: "Flash In Chrome Slow/Lag (Fullscreen Issue)"
date: 2013-03-12
forum: Multimedia Software
---

### Post by bman on 2013-03-12
So for awhile now when I try to play youtube videos in full screen, it's choppy and lagged. Impossible to watch.

I have read around, and none of the solutions fix my problem, most are windows based. The one where you go into the plugins settings and disable one of the flash, well I only have one flash available.

Can't find anymore information. Someone help!

I do have dual monitors, but I am not sure if it started when I got them or if it was already a problem.

---

### Post by sudodus on 2013-03-12
Hi bman,

I suggest that you specify your hardware and flavour of Ubuntu here too, in order to make it easier to give good advice.

I'll be back :-)

---

### Post by bman on 2013-03-12
12.04 Ubuntu

My hardware is fine, I can play them fullscreen sometimes, randomly without issue. AMD graphics.

---

### Post by sudodus on 2013-03-12
> **bman said:**
> 12.04 Ubuntu

My hardware is fine, I can play them fullscreen sometimes, randomly without issue. AMD graphics.

Could it be a problem with the bandwidth of transfer somewhere between  the web-site and your computer? Because of variations in the traffic,  your particular packets of data may arrive fast enough sometimes, but  sometimes they are delayed.

You can check your internet speed (and its variation over time) for example at [[COLOR=#ff0000]http://www.speedtest.net/index.php[/COLOR]]("http://www.speedtest.net/index.php")

It could also be an internal problem. Check with ```
top
``` that the cpu is not running near 100%.

Furthermore, are you running a proprietary driver for the AMD graphics?

---

### Post by bman on 2013-03-12
I am running the open-source drivers. My CPU is not at 100%. It is only youtube I have found out, not other flash based sites.

My speed and hardware are not the problem. As I know I can run it all without issues, has to do with Chrome or Youtube itself. Disabling all related extensions does not do anything either.

---

### Post by sudodus on 2013-03-13
> **bman said:**
> I am running the open-source drivers. My CPU is not at 100%. It is only youtube I have found out, not other flash based sites.

My speed and hardware are not the problem. As I know I can run it all without issues, has to do with Chrome or Youtube itself. Disabling all related extensions does not do anything either.

1. Will the playback quality differ between different instances in time or between different video clips (or both)?

2. Did you test your internet speed at different instances in time with [[COLOR=#ff0000]http://www.speedtest.net/index.php[/COLOR]]("http://www.speedtest.net/index.php")?

3. You can also play the video clips at YouTube with different bitrates (set the player to use smaller frame size or lower bitrate), and check what seems to work the best.

4. And you can try with another browser. Firefox might be slower loading, but maybe the flashplugin-installer will give you a better flash plugin for Firefox.

```
sudo apt-get install firefox
sudo apt-get install flashplugin-installer
```

5. 'internet-speed'

If you want this script, create the directory**[FONT=courier new] /home/$USER/bin[/FONT]** and save the following script code to**[FONT=courier new] /home/$USER/bin/internet-speed[/FONT]** and make it executable. Then check the current receive and send speed (default averaged over 10 seconds). This simple script uses the standard commands **[FONT=courier new]ifconfig[/FONT]** and **[FONT=courier new]bc[/FONT]**. You run the script in an own terminal command window and monitor the current bitrate in kibibits/s (bits/s divided by 1024).

```
#!/bin/bash

if [ "$1" != "" ]
then
 time="$1"
else
 time=10
fi

echo "measuring time $time s; result in kibibits/s (B/s*8/1024)"
echo "     incoming       outgoing     speed:"

inbytes () {
 ifconfig|grep RX|sed -e s/.*RX\ bytes:// -e s/\ .*//|sort -n|tail -n 1
}
outbytes () {
 ifconfig|grep TX|sed -e s/.*TX\ bytes:// -e s/\ .*//|sort -n|tail -n 1
}
ans=""
while test 1
do
in0=$(inbytes)
out0=$(outbytes)
#echo "$in0 $out0"

read -n 1 -s -t $time ans
#sleep $time

in1=$(inbytes)
out1=$(outbytes)
#echo "$in1 $out1"

if [ "$ans" == "q" ]
then
 exit
fi
rxs=$(echo "scale=2; ($in1-$in0)/$time/128" | bc -l)
txs=$(echo "scale=2; ($out1-$out0)/$time/128" | bc -l)
#echo "$rxs $txs"
printf "%13s  %13s\n" $rxs $txs
done

```

---

### Post by bman on 2013-03-17
The quality or size(480 to 1080p) does not matter, my speed is fine and has been.

I don't want another browser, I use Chrome.

---

### Post by sudodus on 2013-03-18
Let us go back and look at the original description of your problem

> **bman said:**
> So for awhile now when I try to play youtube videos in full screen, it's choppy and lagged. Impossible to watch.

I have read around, and none of the solutions fix my problem, most are windows based. The one where you go into the plugins settings and disable one of the flash, well I only have one flash available.

Can't find anymore information. Someone help!

I do have dual monitors, but I am not sure if it started when I got them or if it was already a problem.

1. Will the playback quality differ between different instances in time or between different video clips (or both)?

2. Did you test your internet speed at different instances in time with [[COLOR=#ff0000]http://www.speedtest.net/index.php[/COLOR]]("http://www.speedtest.net/index.php")?

3. You can also play the video clips at YouTube with different bitrates (set the player to use smaller frame size or lower bitrate), and check what seems to work the best. ***Checked***

4. And you can try with another browser. Firefox might be slower loading, but maybe the flashplugin-installer will give you a better flash plugin for Firefox. ***You wrote that you want Chrome (but did you try another one?)***

```
sudo apt-get install firefox
sudo apt-get install flashplugin-installer
```

5. 'internet-speed'

If you want this script, create the directory**[FONT=courier new] /home/$USER/bin[/FONT]** and save the following script code to**[FONT=courier new] /home/$USER/bin/internet-speed[/FONT]**  and make it executable. Then check the current receive and send speed  (default averaged over 10 seconds). This simple script uses the standard  commands **[FONT=courier new]ifconfig[/FONT]** and **[FONT=courier new]bc[/FONT]**. You run the script in an own terminal command window and monitor the current bitrate in kibibits/s (bits/s divided by 1024). [I][B]This script might show if the current connection is too slow (maybe limited at the other end, the youtube server).
[/B][/I]--
You need to check out a few things to be able to find what is causing your problem and to be more or less sure what is *not* causing your problem.

So far it could be the graphics card/driver, or the fact that you have dual monitors, but I don't think we have ruled out the possibility of internet connection problems. So please try to test and check how it works in order to get answers to the questions above :-)

6. And you can try to run the computer with one monitor again to find out how it will play the video clips.

---

### Post by roc6977 on 2013-03-24
Is Pulse Audio installed? If so, try uninstalling and just use Alsa.
sudo apt-get autoremove pulseaudio
sudo apt-get install gnome-alsamixer
reboot since PulseAudio daemon (system service) is also running from the background. 
next time you login to your Desktop you won&#8217;t see the Volume Icon around the system tray area.
to run, type gnome-alsamixer in terminal.

---

### Post by caember on 2013-04-29
Hi, I have the same issue.
Tried unistalling pulseaudio, but it didn't work - maybe because I use 13.04.

Also, another thing - it definitely is something with pepperflash (google's flash) and youtube:
Other flash based things in the web work absolutely fine in fullscreen, whereas youtube, it gets really choppy.
Interesting fact, I have html5 enabled in youtube, so those videos with html5 support also work flawlessly.

What I also did try was to use the original, outdated flash - which is the same in chrome and firefox - and has another, pretty stupid problem:
It won't load the video unless you pause it. If you try to play it, it stops buffering. Why, adobe. Just why. This is not my connection.

If anyone has a suggestion, it would be really appreciated.

edit, with 'choppy', I mean not enough fps, as compared to 'stuttering', which means connection based problems

---

### Post by schnelle on 2013-10-02
Enabling "Override software rendering list" in chrome:flags fixes the problem for me. 

Hope it helps someone :)

---

### Post by Coffey50 on 2013-12-09
Hey, I had this same issue and here was the fix that got mine to work ! 

Make sure you have the flash player for mozzilla firefox installed via the Ubuntu Store ! 

Then start up chrome and type > [chrome://plugins/](chrome://plugins/) and look to the right hand side of the screen where it says > +Details
[ATTACH=CONFIG]248475[/ATTACH]

Now scroll down until you see > [COLOR=#000000][FONT=Ubuntu]**Adobe Flash Player**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu](2 files)[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]- Version: 11.2 r202[/FONT][/COLOR] 

Now there will be two options, you want to disable the one that says: 
> Name: Shockwave Flash
Description: Shockwave Flash 11.9 r900
Version: 11.9.900.170
Location: /opt/google/chrome/PepperFlash/libpepflashplayer.so
Type: PPAPI (out-of-process)
Enable
MIME types: 
MIME type Description File extensions
application/x-shockwave-flash Shockwave Flash 
.swf
application/futuresplash FutureSplash Player 
.spl

That'll have a highlighted blue text that says > _[COLOR=#0000ff]Disable[/COLOR]_
Go ahead and click on that ! 
Now that you've disabled it, that section should be greyed out and the entry underneath it that says: 
> Name:    Shockwave FlashVersion:    11.2 r202
Location:    /usr/lib/flashplugin-installer/libflashplayer.so
Type:    NPAPI
      Disable
MIME types:    
MIME type    Description    File extensions
application/x-shockwave-flash    Shockwave Flash    
.swf
application/futuresplash    FutureSplash Player    
.spl


[ATTACH=CONFIG]248476[/ATTACH]
I'll include a picture of what it should look like, but once you've done this it's time to restart Chrome and enjoy your fullscreen Flash Videos.

---

### Post by Geancarlo on 2014-04-07
> **schnelle said:**
> Enabling "Override software rendering list" in chrome:flags fixes the problem for me. 

Hope it helps someone :)

This solved it for me. Thanks.
Radeon 5770 on running AMD w/ 4GB ram 

WattOS 7.5 (Ubuntu 13.04)

---

### Post by Exilvin on 2014-04-23
> **schnelle said:**
> Enabling "Override software rendering list" in chrome:flags fixes the problem for me. 

Hope it helps someone :)

Finally a solution to this annoying problem! After weeks of searching to solve my problem, this is the only solution that works great for me. Thank you schnelle :D .

---

### Post by jim86 on 2015-01-26
SOLVED ! %            

chrome:flags

Enable  [COLOR=#000000][FONT=Noto Sans]**Override software rendering list**[/FONT][/COLOR][COLOR=#000000][FONT=Noto Sans]Mac, Windows, Linux, Chrome OS, Android     restart Chrome  100  % fixed Enjoy ^^:)

no need not to use the latest flash google flash is very good do that step all will work great [/FONT][/COLOR]

---

### Post by badtlc on 2015-01-27
I have this same problem with HTML5 and flash videos with chrome.  It doesn't see hardware acceleration for anything when you go to chrome:gpu.  I have intel graphics.  Is there anything else to try?

---

