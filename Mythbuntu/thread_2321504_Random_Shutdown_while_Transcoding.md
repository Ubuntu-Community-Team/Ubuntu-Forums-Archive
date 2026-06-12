---
title: "Random Shutdown while Transcoding"
date: 2016-04-22
forum: Mythbuntu
---

### Post by azmanam2 on 2016-04-22
AMD Phenom II 3.4GHz Quad-Core Processor
 16 GB RAM
 1.5 TB Western Digital SATA Hard Drive
 ASUS GeForce GT440 1GB Video Card
 Hauppauge HVR-1600 Tuner Card
 Creative Sound Blaster X-Fi Card

I am going through and manually transcoding all my saved TV episodes to permanently remove the commercials as per this site: [https://www.mythtv.org/wiki/Removing_Commercials#Removing_commercials_using_mythfrontend](https://www.mythtv.org/wiki/Removing_Commercials#Removing_commercials_using_mythfrontend)

Sometimes it works fine, sometimes halfway through it completely shuts down my computer without warning.

My first thought was obviously overheating. I've blown it out with compressed air already. Looking at psensor, though, the highest temperature on any processor is ~65 degC. When it transcodes without shutting down, it can handle this temperature just fine, then cools down again once transcoding is complete. Further, when it does shutdown, the temperature is usually not above ~55 degC.

Once it shuts down, if I try to restart right away, it won't make it through the startup routine without randomly shutting down again - again making me think overheating, but psensor just doesn't support that.

Thus usually happens after the computer's been idle for a while. Top and iotop don't show anything out of the ordinary, though. Top will show >100% cpu usage during transcoding, but this is not determinate for shutdown - sometimes it handles it just fine, sometimes it shutsdown.

HELP!

---

### Post by TheFu on 2016-04-23
CPU isn't the only chip in the box.  Check for thermal issues on the north and south-bridges too.  Also, the GPU.

Could also be a failing PSU ... once had a failing GPU show the same issues.  Pulled that out and the machine with the same PSU, MB, CPU has been running about 5 yrs.

Why manually transcode?  There are ways to script that and to push new jobs onto a queue to be run after the previous one finishes.
* TaskSpooler; handles the batch queue.
* HandBrakeCLI; setup the presets you want in the GUI and use those with the CLI version.

I used ffmpeg and mencoder and avconv and ... and .... and for years before switching to HandBrakeCLI.
Scripting is pretty easy. I've posted some of these scripts in these forums before.

---

### Post by azmanam2 on 2016-04-23
Thanks for the response :smile:

GPU temp looks in normal range. Here are the min/max temps after having  the computer on and idle for a while and successfully transcoding some  episodes:

```
CPU: 26 - 61
MB: 22- 43
temp1: 34 - 73
GPU: 21 - 40
```

  *temp1 is: k10temp-pci-00c3 adapter: PCI adapter

Other output from sensor:

```
Vcore voltage: 1.41V (0.8 - 1.8V)
3.3V Voltage: 3.33V (2.97 - 3.63V)
5V Voltage: 4.97 (4.5 - 5.5V)
12V Voltage: 11.78 (10.2 - 13.8V)
CPU FAN speed: 4017 (3110 - 5720RPM)
cpu usage: 0% - 69%
```

hddtemp: ```
32 degC
```

How do I check the north/south bridge? Is there a way to check the PSU?

This morning, after coming back from idle, it shutdown just scrolling  through the episode list. No transcoding or anything was taking place at  the time.



Here is the last few lines of /var/log/syslog at the point of the last random shutdown:

```
Apr 23 17:09:01 ****-MythTV CRON[3897]: (root) CMD (  [ -x  /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ]  && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean  /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Apr 23 17:17:01 ****-MythTV CRON[3924]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 23 17:38:59 ****-MythTV kernel: [28830.277740] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:38:59 ****-MythTV kernel: [28830.277745] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:39:02 ****-MythTV CRON[3973]: (root) CMD (  [ -x  /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ]  && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean  /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Apr 23 17:27:15 ****-MythTV mythbackend: message repeated 2 times: [  mythbackend[2135]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire:  CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min]
Apr 23 17:45:32 ****-MythTV kernel: [29223.115337] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:45:32 ****-MythTV kernel: [29223.115350] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:39:21 ****-MythTV mythfrontend.real: message repeated 3 times:  [ mythfrontend[1783]: E ImageLoad mythuihelper.cpp:1311  (LoadScaleImage) MythUIHelper:  LoadScaleImage(/var/lib/mythtv/recordings/1201_20160407060000.mpg.png)  Unable to find image file]
Apr 23 17:46:32 ****-MythTV kernel: [29282.603720] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:46:32 ****-MythTV kernel: [29282.603725] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:47:32 ****-MythTV kernel: [29342.325987] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:47:32 ****-MythTV kernel: [29342.325992] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:48:31 ****-MythTV kernel: [29402.058885] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:48:31 ****-MythTV kernel: [29402.058898] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:49:35 ****-MythTV kernel: [29465.384030] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:49:35 ****-MythTV kernel: [29465.384036] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:50:34 ****-MythTV kernel: [29524.990718] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:50:34 ****-MythTV kernel: [29524.990732] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:51:37 ****-MythTV kernel: [29587.837817] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:51:37 ****-MythTV kernel: [29587.837830] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:52:37 ****-MythTV kernel: [29647.734199] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:52:37 ****-MythTV kernel: [29647.734203] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:53:40 ****-MythTV kernel: [29710.795696] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:53:40 ****-MythTV kernel: [29710.795710] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Apr 23 17:54:40 ****-MythTV kernel: [29770.621400] atkbd serio0: Unknown  key released (translated set 2, code 0x81 on isa0060/serio0).
Apr 23 17:54:40 ****-MythTV kernel: [29770.621413] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
```



I manually transcode because the episodes of Seinfeld I tape don't flag  commercials at the beginning and end very well, so I have to manually  edit the cut list first. :smile:

---

### Post by TheFu on 2016-04-23
Keyboard issue?  As for getting temps - there are different sensor settings for every different motherboard made. You'll have to set those up.  I'd be looking elsewhere.

I use comskip to find commercials overnight, then (cough) VideoReDo (cough) to validate and save the files as MPEG2 (recoding streams here are mpeg2) w/o any commercials, then let the automatic transcoding go to town on Linux.  Everything that can be batched, is.  Takes about 30sec per file to fix/validate commercial locations.  [http://blog.jdpfu.com/2011/10/20/commercial-removal-from-wtv-recordings](http://blog.jdpfu.com/2011/10/20/commercial-removal-from-wtv-recordings) is a little old, but describes some of it.  I find that comskip runs faster on Linux than under Windows.  I even have CC1 and CC3 SRT files created from the mpeg stream and added for some telenovellas. ;)  If CC3 doesn't exist and CC1 is Spanish, I'll generate a bad translation using apertium and add that to the resulting mkv file(s). ;) [http://blog.jdpfu.com/2012/06/06/cc3-closed-captions-solved-i-feel-dumb](http://blog.jdpfu.com/2012/06/06/cc3-closed-captions-solved-i-feel-dumb) explains the caption processing.  I figure it is worth adding, since my hearing isn't likely to stay perfect for the next 50 yrs.

---

### Post by azmanam2 on 2016-04-23
Thanks for the quick reply. It's the same keyboard I've been using forever. I'll look into it.

The links are 403'd forbidden, btw.

---

### Post by TheFu on 2016-04-23
403 means one of these things:
* Win10.  Use a Linux browser.
* Abusive subnet at the ISP.

Ways around it is to use a proxy/vpn, grab a cached versions or visit the **wayback machine** for a mirror of the site.

The log shows multiple atkbd events that don't make sense, hence the keyboard comment.  I'd unplug and replug it to start. See if that helps. Try a different port - if PS2, try a USB adapter.  Those log entries are NOT normal. [http://ubuntuforums.org/showthread.php?t=1787724](http://ubuntuforums.org/showthread.php?t=1787724) is a little old, but the same issue, solved.  Seems a reinstall was needed.  I'd look for corrupted packages and see what can be reinstalled.  There are a few dpkg and apt-get check commands which show that stuff.  Don't remember them off the top of my head, but the manpage for each covers it.  Look for "check"

---

