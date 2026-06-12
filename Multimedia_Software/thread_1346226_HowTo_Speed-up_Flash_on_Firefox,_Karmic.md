---
title: "HowTo Speed-up Flash on Firefox, Karmic"
date: 2009-12-04
forum: Multimedia Software
---

### Post by dentaku65 on 2009-12-04
Here some useful tricks (collected around) to speed-up Flash on Firefox

**1) Remove and install flash plugin stuff**
```
sudo apt-get --purge remove gnash adobe-flashplugin swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```
**2) Optimize Firefox**
Open Firefox
```
Choose the menu Edit -> Preferences -> Advanced -> Network -> Connection -> Settings
and choose No proxy option, then click Ok, then Close
```
In the address bar type **about:config** and filter/change the following settings:
```
network.dns.disableIPv6 true
network.http.max-connections 96
network.http.max-connections-per-server 32
network.http.max-persistent-connections-per-server 6
network.http.pipelining true
network.http.pipelining.maxrequests 8
```
Install Flashblock extension (specially for slower PC): [https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

Close Firefox

**3) Set OverrideGPU**
```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" > ~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```
This setting is valid only for Youtube site

**4) Set CPU Threshold on ondemand**
```
sudo gedit /etc/init.d/ondemand
```
You should see in the file something like this, add this part (red):
```
	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done

[COLOR="Red"]	for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
	do
		[ -f $CPU_THRESHOLD ] || continue
		echo -n **40** > $CPU_THRESHOLD
	done[/COLOR]
```

Please note that **40** (means %) is indicative; see the article [http://linux.digitalsp.com/2009/08/improving-stuttering-during-flash-video.html]("http://linux.digitalsp.com/2009/08/improving-stuttering-during-flash-video.html")

**5) Disable XGL**
```
mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable
```
**6) Remove and prevent nasty flash cookies**
Open a terminal window and close firefox

Check how many cookies you have
```
cd
find -iname '*.sol' | wc -l
```
Delete them
```
find -iname '*.sol' -exec rm "{}" \;
```
Prevent further flash cookies on your machine
```
chmod -Rv 0500 ~/.macromedia/Flash_Player/#SharedObjects/ ~/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/
```
See this great article on it. [http://www.linuxplanet.com/linuxplanet/tutorials/6709/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6709/1/)
Consider that applying chmod 500 on dirs some flash site can be difficult to load; an alternative way can be to delete the Flash cookies periodically:
```
sudo rm -R ~/.macromedia/
```
**7) Disable Pango**
Edit this file 
```
gedit ~/.bashrc
```
and add this line at the end:
```
export MOZ_DISABLE_PANGO=1
```
Save and close.

Reboot your box and enjoy flash video.

---

### Post by komasoftware on 2009-12-07
Before, I was reading up on this topic all over the web and I made some of the suggested changes. You seem to bundle alot of info scattered over several blogs;
Now, I followed all instructions, and at first glance, it does seem to make a difference. 

thx for efforts.

---

### Post by akwala on 2010-01-05
Re preventing flash-cookies/LSO, this is a handy FF ad-on: [https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)

---

### Post by rimshot4 on 2010-01-31
This trick worked for me, thanks!

---

### Post by Eyeron on 2010-02-17
Thanks now my firefox is awfully slow. Wish there was a way to reset all these changes.

---

### Post by Elludium_Q-36 on 2010-04-25
You're kidding right, "Eyeron"?

Prior to effecting changes, firefox drug my Jaunty system down to the 9th circle, making it UNUSABLE.  Killing the power was often the only way to reset, unless one wanted to wait for it to release the system.  This was even with scripts blocked by no-script and with flashblock in place.

I have currently reverted to Kubuntu 8.04.2 and there is no file:  /etc/init.d/ondemand so that can't be edited.  Also, alt+F2 does NOT bring up a system monitor to kill processes on a locked system so these suggested modifications are most welcome!!!

I've read of swiftfox [ [http://getswiftfox.com/](http://getswiftfox.com/) ] elsewhere in the forums but the repository they list is still in unstable and I see no mention of a gpg public key.

---

### Post by runeh76 on 2010-11-28
Package manager ---remove Flashplugin-nonfree
                             And if u dont use Ati-display card also remove  xserver-xorg-video  plaa plaa plaaa things, where u can find any ati support.

Check ur adobe flashplayer settings manager things and clear all saved stuff ---http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html

Disable plugins, left only flash&java --update if necessary

Put these ur dns servers   208.67.222.222, 208.67.220.220

There u are  :cool:   ...no more lagging flash and mouse pointer, when playing flash-games. And net gonna working much faster.

Cheers Runeh76  (32bit Maverick)

---

