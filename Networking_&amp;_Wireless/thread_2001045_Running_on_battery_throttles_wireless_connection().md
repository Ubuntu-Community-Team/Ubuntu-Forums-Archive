---
title: "Running on battery throttles wireless connection(?)"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by taylorkh on 2012-06-10
I have just installed Ubuntu 12.04 on a Dell Latitude 2100. I installed the Broadcomm driver and configured my hidden wireless network. All is well. However, if I run the netbook on battery the wireless network speed decreases drastically. I have a script which performs an ftp dowload from my ISP's test server. With the charger connected and powered on I get 340 - 350 KB/sec which is what my DSL generally provides. If I power off the charger the download speed drops to 85 KB/sec.  I have confirmed this several times and reinstalled the OS. No difference. File transfers to/from the nebook over my home network are similarly slow when the netbook is running on battery.

netstat -ie shows a few dropped packets on TX when running on battery. However, the number is lower than when running on the charger.

The speed of the wired connection is NOT effected. It is the same on battery or on charger.

This is NOT a problem on 10.04 which I have been running on the machine for the past couple of years. I have reinstalled 10.04 and confirmed this. I do not recall it being an issue with 9.04 which was on the machine from the factory.

It seems that something in power management is impacting the wireless card. The wireless icon in the notification area shows 100% on battery and the machine is only about 4 feet from the wireless router. I do not see anything in the power settings dealing with this.

Does anyone have any ideas?

TIA,

Ken

p.s. Had I been looking I would have seen that your are in the UK and I am sure you are familiar with the Price of (electrical) Darkness.  Thanks again!

---

### Post by AnotherMuggle on 2012-06-10
> **taylorkh said:**
> I have just installed Ubuntu 12.04 on a Dell Latitude 2100. I installed the Broadcomm driver and configured my hidden wireless network. All is well. However, if I run the netbook on battery the wireless network speed decreases drastically. I have a script which performs an ftp dowload from my ISP's test server. With the charger connected and powered on I get 340 - 350 KB/sec which is what my DSL generally provides. If I power off the charger the download speed drops to 85 KB/sec.  I have confirmed this several times and reinstalled the OS. No difference. File transfers to/from the nebook over my home network are similarly slow when the netbook is running on battery.

netstat -ie shows a few dropped packets on TX when running on battery. However, the number is lower than when running on the charger.

The speed of the wired connection is NOT effected. It is the same on battery or on charger.

This is NOT a problem on 10.04 which I have been running on the machine for the past couple of years. I have reinstalled 10.04 and confirmed this. I do not recall it being an issue with 9.04 which was on the machine from the factory.

It seems that something in power management is impacting the wireless card. The wireless icon in the notification area shows 100% on battery and the machine is only about 4 feet from the wireless router. I do not see anything in the power settings dealing with this.

Does anyone have any ideas?

TIA,

Ken

Have you tried the following in a terminal?:
```
sudo iwconfig wlan0 power off
```

---

### Post by taylorkh on 2012-06-10
Thanks AnotherMuggle,

Tried that and got> Error for wireless request "Set Power Management" (8B2C)
SET failed on device wlan0 ; No such Device
Also tried wlan1 just in case, same result. Then, having engaged my brain, I had a look at ifconfig. The wireless connection is eht1 which I knew but did not register. iwconfig showed> 
ken@taylor13:~$sudo ifwconfig eth1 

eth1      IEEE 802.11bg  ESSID:"Luca$Electric"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:F2:7D:77:3C   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit : 7   RTS thr : off   Fragment thr : off
          Power Managementmode : All packets received
          Link Quality=5/5  Signal level=-34 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0After running the command against the correct device I find that > Power Management : offand my connection is back to full speed on battery.

A thousand THANK YOUs!!!

Ken

p.s. You would appreciate the name of my wireless network if you ever owned a British car :P

---

### Post by AnotherMuggle on 2012-06-10
> **taylorkh said:**
> Thanks AnotherMuggle,

Tried that and got
Also tried wlan1 just in case, same result. Then, having engaged my brain, I had a look at ifconfig. The wireless connection is eht1 which I knew but did not register. iwconfig showedAfter running the command against the correct device I find that and my connection is back to full speed on battery.

A thousand THANK YOUs!!!

Ken

p.s. You would appreciate the name of my wireless network if you ever owned a British car :P

You will notice that the speed will be back slow again after a reboot.  To make the change permenant you need to add that line to a startup script.

A common thing to do is to add the command to the file /etc/rc.local just before the line which says "exit 0"

---

### Post by taylorkh on 2012-06-10
I think Ubuntu was written by Lucas Electric. I just finished a g4l restore of my prior installation of Ubuntu 12.04 with all my desired software installed, set to gnome-session-fallback etc.  

sudo iwconfig eth1 shows Power Management : Off. However, the "slow on battery" symptom is there. The power off command again fixes the problem. However, I see nothing changed.

I have edited /etc/rc.local and rebooted. But that did not work???

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
iwconfig eth1 power off

exit 0
```I tried it without the sudo as the file is owned by root. It is executable > ken@taylor13:~$ ll /etc/rc.local
-rwxr-xr-x 1 root root 335 Jun 10 14:46 /etc/rc.local*
ken@taylor13:~$ 
I added sudo to the line and rebooted again. Still nothing.  I added these lines to make sure the script executed ```
touch /home/ken/Desktop/i_ran
sudo touch /home/ken/Desktop/sudo_ran

```and I find these two files on my Desktop and they are owned by root. Is the script running before the interface is up? I suspect that has something to do with it not making the configuration change. 

Is there a way to force the wireless connection up earlier? It does come up prior to my logging into the computer. I can connect over the wireless network with ssh before I login.

Ken

---

### Post by taylorkh on 2012-06-11
Well, after some searching and cussing I have found a more permanent fix.  The key is not to try and accelerate the loading of the wireless network. I was going down the ifup route but that seems to be depreciated and not the way to go. I found the answer here [URL=http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on[/URL]
I used the second approach > Than to make it permanent run command as follows:

1.cd /etc/pm/power.d

2.sudo gedit wifi_pwr_off

This will open an empty file, copy the code below into it:

#!/bin/sh 
/sbin/iwconfig wlan0 power off

3.Save the file, remember to

sudo chmod +x wifi_pwr_off

and restartWorks like a champ!!!

And again my thanks to AnotherMuggle for pointing me in the direction of iwconfig.

Ken

p.s. not sure why the link I inserted does not act as a link. If you copy/paste it it will bring up the page.

---

