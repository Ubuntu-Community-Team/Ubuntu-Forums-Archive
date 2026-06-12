---
title: "Problem connecting wirelessly via command line"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by ilikeyourflannel on 2010-05-11
For reasons that are not terribly interesting I decided it would be a great idea to remove and re-install the xserver-xorg package.  Which proved to be a much larger mistake than I imagined it would be.  I purged the package, and then restarted.    Naturally I need to have an internet connection to use apt-get to reinstall xserver-xorg, which is where my idea falls apart.  

I followed the directions in the [How To: Manual Network Configuration]("http://ubuntuforums.org/showthread.php?t=571188").  However, after I enter the command "sudo dhclient wlan1" I get the line "wmaster0: unknown hardware address type 801" twice prior to the output that the above link shows.  Then I just get DHCPDISCOVER messages until I get a "No DHCPOFFERS received. No working leases in persistent database - sleeping."

I'm connecting with WEP to a router that I know works (because I'm using it to type this on my laptop right now) and I know that the wireless adapter(RTL8187) is installed properly because it automatically connected to my network when I had xserver-xorg still installed.  I'm running ubuntu 9.04.

I've searched for a few hours and I'm no closer to resolving the issue.  Any advice/suggestions would be greatly appreciated!  Thanks!

---

### Post by ilikeyourflannel on 2010-05-12
Does anyone know why it would be working while using network manager to automatically connect, and the command line fails to connect?

The command sequence I'm running is:

sudo ifconfig wlan1 down
sudo dhclient -r wlan1
sudo ifconfig wlan1 up
sudo iwconfig wlan1 essid "essidname" key AABBCCDDEEFF mode Managed
sudo dhclient wlan1

I never get past DHCPDISCOVER, anyone know whats going on?  Does removing xserver-xorg somehow change my driver? The wireless card was working just fine before this...

---

### Post by chili555 on 2010-05-12
If iwconfig shows that the mode is managed, you don't need to declare it again. Your commands look sound. 

It may be just the way you disguised your key, but you have 12 characters. A HEX key would have 10 or 26. Did you double-check the encryption key?

---

### Post by ilikeyourflannel on 2010-05-12
Thanks for the advice.  I did double check my key, and I'm entering it correctly.  Just as you thought I make a mistake in disguising it.

One other thing I just noticed, right before I removed xserver-xorg I changed my hostname.  Now whenever I use sudo I get the message "sudo: unable to resolve host [current-host-name]" - but the sudo command seems to work just fine.  I thought this might be contributing to the issue, so I changed the hostname back to the original.  And I still get the message after I use sudo.  I'm not concerned about that issue unless it's related to connecting wirelessly.

Any thoughts are welcome.  I'm grasping at straws here!

---

### Post by chili555 on 2010-05-12
> changed the hostname back to the original.Where? /etc/hosts, /etc/hostname or, ideally, both? It may take a reboot to get any changes to stick fully.

---

### Post by ilikeyourflannel on 2010-05-12
Both times I only changed the hostname in /etc/hostname.  And now I know what to do in the future - thanks!  

On closer inspection when I changed /etc/hostname back to the "original" it had a typo.  I corrected it & rebooted.  Now it lines up with what's in /etc/hosts so the message disappeared.  But I still can't connect.

I thought I had figured out the issue, maybe I did but i'm missing something.  About a month ago I changed my user password.  I noticed that whenever I restarted my computer I was prompted for my old password by (i think) network manager.  Once I entered it I was able to connect.  I changed my password back to the original, but  it's still not connecting.  

Any ideas?

---

### Post by chili555 on 2010-05-12
The password should only be an issue if Network Manager is running; it should not be running in single user mode, that is, without X server. Check with:```
ps aux | grep -i Network
```I hope you do not see:> $ ps aux | grep -i network
root       716  0.0  0.3  18648  3920 ?        Ssl  22:18   0:00 [COLOR="Blue"]NetworkManager[/COLOR]
root      1418  0.0  0.0   2228   980 ?        S    22:18   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth1.pid -lf /var/lib/dhcp3/dhclient-d16e7090-6fee-4b9d-b5c0-04c9cd418c8f-eth1.lease -cf /var/run/nm-dhclient-eth1.conf eth1
chili     1656  0.0  0.0   3324   856 pts/0    S+   22:26   0:00 grep -i network
May I see:```
iwconfig
```Also, is the behavior improved if you separate the commands:```
sudo iwconfig wlan1 essid "essidname"
sudo iwconfig wlan1 key AABBetc.
sudo dhclient wlan1
```Also, I have sometimes had better luck with lower case letters; i.e. 096c7fetc. rather than 096C7F...

---

### Post by ilikeyourflannel on 2010-05-13
iwconfig: ```

lo              no wireless extensions.

eth0           no wireless extensions.

pan0          no wireless extensions.

wmaster0   no wireless extensions.

wlan1         IEEE 802.11bg ESSID:""
                 Mode: Managed    Frequency:2.412 GHz    Access Point:  Not-Associated
                 Tx-Power= 20dBm
                 Retry min limit:7       RTS thr:off         Fragment thr=2352 B
                  Power Management:off
                Link Quality:0     Signal level:0    Noise level:0
                  Rx invalid nwid:0    Rx invalid crypt:0   Rx invalid frag:0
                  Tx excessive retries:0     Invalid misc:0     Missed beacon:0
```Unfortunately I do see what you hoped I didnt.

```
$ps aux | grep -i Network

root        3241     0.0  0.1       8208   2656 ?     Ss  16:27   0:00  /usr/sbin/NetworkManater --pid-file  /var/run/NetworkManager/NetworkManager.pid
root        3261     0.0   0.1      6948   3124 ?     S     16:27   0:00  /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
[user]     3655     0.6   4.6   299224 96164 ?    SN1 16:27 1:54 java  -Dnetworkaddress.cache.ttl=0 -Dnetworkaddress.cache.negative.ttl=0 -enableassertions:freenet -Xms60m -Xmx128m -Djava.library.path=lib -classpath freenet.jar:freenet-ext.jar -Dwrapper.key=nZa_IyOU0cf1A0HH -Dwrapper.port=32000 -Dwrapper.version=3.2.3 -Dwrapper.native_library=wrapper -Dwrapper.ignore_signals=TRUE -Dwrapper.service=TRUE -Dwrapper.cpu.timeout=10 -Dwrapper.jvmid=1 freenet.node.NodeStarter freenet.ini
[user]      10718  0.0  0.0        3336  868  tty1   R+  21:11 0:00 grep -i Network
```I tried connecting with both upper and lowercase letters as well as separating the commands, no luck.  Thanks for your help with this Chili!

---

### Post by chili555 on 2010-05-13
Yikes! That Network Manager is pervasive, isn't it? I have had an ongoing discussion with one of the forum moderators about the interaction of NM and manual configuration. This will add more fuel to the discussion.

You might try stopping NM first.```
sudo /etc/init.d/NetworkManager stop
```Try the command again:```
ps aux | grep -i Network

```Make sure it's really stopped and then try your commands again.

---

### Post by ilikeyourflannel on 2010-05-13
I tried the command "sudo /etc/init.d/NetworkManager stop" and it replied "  *  Stopping network connection manager NetworkManager             [  OK  ]"

When I run "ps aux | grep -i Network" the output is the same, except for the line "root        3241     0.0  0.1       8208   2656 ?     Ss  16:27   0:00  /usr/sbin/NetworkManater --pid-file  /var/run/NetworkManager/NetworkManager.pid" is removed.  All other lines are still present.

I am still not able to connect.  Gives me the same output as before...  We've got to be getting close!

Just in case it helps -  When the "DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5" shows up I noticed the interval numbers are not in order.  Sometimes the interval even repeats the same number.  For example, the last time I tried to connect the numbers were 5,7,13,11,7,12, and 6.  

Thanks again for your help!

---

### Post by chili555 on 2010-05-13
I was able to do it just now on my own system. Here is what I did.```
sudo apt-get remove network-manager*
``````
sudo gedit /etc/network/interfaces
```Add the following stanza:```
auto wlan1
iface wlan1 inet dhcp
wireless-essid mylilrouter
wireless-key 0123456789
```Proofread, save and close gedit. Reboot.

I was and am connected on boot.

It's a bit radical, I know, but it works.

---

### Post by ilikeyourflannel on 2010-05-14
Awesome!  Just like you said I was connected on start up.  I'm downloading xserver-xorg as I type this.   Thanks so much for the help!

---

