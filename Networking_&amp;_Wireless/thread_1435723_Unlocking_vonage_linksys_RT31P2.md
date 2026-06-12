---
title: "Unlocking vonage linksys RT31P2"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by siquad on 2010-03-21
I couldn't find any details on how to do this on Ubuntu, so I figured I'd share for anybody who needs to do that.

I got this adapter from a garage sale, it's meant for use with vonage service, it has a web interface with disabled voice tab, and a hidden voice admin page. My goal was to access (unlock) those pages, so that I can use it with one of the free sip providers.

The main thread on how to do this is over at bargainshare forums, the only thing I'm adding here is how to do it on Ubuntu as opposed to windows:
[http://www.bargainshare.com/index.php?showtopic=88743]("Linksys RT31P2 and WRT54GP2 Unlock Guide")
I will write the simplist path using typical defaults, if your setup deviates or if one of the steps below fails, please refer to the original guide at this link to sort things out.

[COLOR="Red"]Important note: the pc used in the procedure shouldn't be connected to the internet. Internet access is only needed to get files, programs and instructions, either before using the pc for this procedure, or through a separate pc.[/COLOR]

**Adapter setup:**
[LIST]
[*]Do NOT connect the adapter to the internet especially if it has been out of service for a while.
[*]Connect an ethernet cable to one of the lan ports on the adapter and in a browser go to 192.168.15.1, this is the default lan gateway address. When prompted to log in use admin/admin again that's the default
[*]First thing needed is to flash a special unlocking firmware that allows the adapter to acquire clear text configuration file (as opposed to the encrypted vonage one). After downloading the unlocking firmware from guide above, go to the Administration page then the tab for flashing firmware. Select the firmware file you just saved and let it flash, you'll be prompted to log in, I used user/7756112 , more can be found in the guide, if successful, you'll get a message to that effect. Now firmware version should be 1.7.02 and voice 2.09 LId
[*]Next we need to get the adapter to get our configuration file, create one as mentioned in the guide above, meister_sd method, put the file in a folder of your choice, we'll need to use that as our tftp root folder later
[*]Now we configure the adapter to talk to the pc, under the setup page of the adapter set "Internet Connection Type" to Static IP and assign the adapter a static IP address, e.g. 192.168.1.88, then set the default gateway and DNS1 to a static IP address that you'll later assign to your PC, make sure it's on the same subnet as the IP address you assigned to the adapter, e.g. 192.168.1.99, save the changes
[*]Switch the ethernet cable to the wan port of the adapter, so it's connected directly to the pc, no crossover cable needed in my experience, turn off the adapter until we setup the pc
[/LIST]
[B]
PC setup:[/B]
[LIST]
[*]First we need dnsmasq package from synaptic. This package can provide dns, dhcp, read only tftp daemons, outstanding piece of software. during the installation, it will automatically start with it's default settings. we'll shut it down so that we can start it with different command line options:
```
sudo /etc/init.d/dnsmasq stop
```
[*]Now we configure the pc to act as a gateway and dns server temporarily, System->Preferences->Network connections , then edit the ethernet interface we're using to connect to the adapter, under IPv4 settings, set the method to manual, then add an address entry with the IP address used on the adapter for dns and gateway, ie 192.168.1.99 and gateway and dns as 127.0.0.1
[*]Now we need to start the dns and tftp daemons:
```
sudo dnsmasq -q --enable-tftp --tftp-root=<your tftp absolute root,eg /home/tftp_root>, --address=/ls.tftp.vonage.net/vonage.net/voncp.com/192.168.1.99
```
this command starts the daemons with the the given tftp root, and tells the dns daemon to translate the two domains mentioned to the pc address, don't be tempted to use 127.0.0.1 for the address, didn't work for me
[*]To confirm that the daemons are monitoring the ports as needed, run the following commands:
```
sudo netstat -anlp | grep -w 53
sudo netstat -anlp | grep -w 69
```
The first checks for who's listening on port 53, for dns service, the second for tftp 69. A good output would like like:
```
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      10773/dnsmasq   
tcp6       0      0 :::53                   :::*                    LISTEN      10773/dnsmasq   
udp        0      0 0.0.0.0:53              0.0.0.0:*                           10773/dnsmasq   
udp6       0      0 :::53                   :::*                                10773/dnsmasq
```
and
```
udp        0      0 0.0.0.0:69              0.0.0.0:*                           9284/dnsmasq
```
[*]Now that the daemons are running, start the log file viewer from System->Administration and go to the syslog tab, that's the default logging mechanism for dnsmasq, and where we'll be able to see incoming dns and tftp requests from the adapter (wireshark is of course the ultimate tool if you want far more details, but for this tutorial, the log is suffecient)
[/LIST]

**Watch it happen:**
[LIST]
[*]Now start the adapter, you should start seeing dns requests show up in the log, within a few seconds, a dns lookup will come for ls.tftp.vonage.net which is the server from which the adapter gets its provisioning (xml file)
[*]At this point, you should see dnsmask reply to the effect of:
```
dnsmasq[10804]: config ls.tftp.vonage.net is 192.168.1.99
```
[*]Next the adapter will try to get the xml file you created, however most likely it will look for a subfolder under the root tftp folder with some cryptic name, since that lookup will fail, what it's looking for will be printed in the log, mine looked like this:
```
dnsmasq-tftp[9768]: TFTP file /home/tftp_root/xxxxxxxx/spayyyyyyyyyyyy.xml not found
```
obviously, I replaced the actual subfolder name and my mac address with x,y. now we just need to create that folder structure as expected
[*]Once the structure is in place, power cycle the adapter
[*]Now it should go through the same sequence, except that it will find the file it's looking for, and it will grab it like so:
```
dnsmasq-tftp[10804]: TFTP sent /home/tftp_root/xxxxxxx/spayyyyyyyyyyyy.xml to 192.168.1.88
```
[*]That's it, the adapter should now be unlocked, now don't forget to get your manufacturer original GPP_K key as detailed in the guide linked above...
[/LIST]

---

### Post by b.shah on 2011-09-11
I want to unlock my vonage RT31P2 router, can you help me how do it step by step or do u have any video so that i can see and do that. What you have written in your previous post seems be solving the problem however i am finding difficult to understand, let me know from where do i start and how do i unlock.
Thanks in Advance.

---

### Post by agapedisciple on 2012-08-26
Great post! I finally got this box unlocked after many unsuccessful tries via windows. I also ran into issues with your method, but finally found the solution and put it in the post below:

First off, I used [pendrivelinux.com]("http://www.pendrivelinux.com/") to make a bootable Linux USB drive. (I used "ubuntu-10.10-desktop-i386.iso" since I downloaded it a while back. Any newer version should work.)  Once in Linux, I followed the above instructions. My first issue was that I didn't install the full version of **dnsmasq. **To do so, use the synaptic package manager in System -> Preferences. Then goto Settings -> Repositories and select all of the sources in "Ubuntu Software" and "Other Software" *except *the source code repositories. Now you should be able to search for the full **dnsmasq**, mark it and install it.

Second, there is a bug in the command listed below. (Or at least it never worked properly for me.)
> **siquad said:**
> 
[LIST]
[*]Now we need to start the dns and tftp daemons:
```
sudo dnsmasq -q --enable-tftp --tftp-root=<your tftp absolute  root,eg /home/tftp_root>,  --address=/ls.tftp.vonage.net/vonage.net/voncp.com/192.168.1.99
```this  command starts the daemons with the the given tftp root, and tells the  dns daemon to translate the two domains mentioned to the pc address,  don't be tempted to use 127.0.0.1 for the address, didn't work for me
[/LIST]

After much research, I found that there should **not** be a comma after the "--tftp-root" location. So here is the corrected code that worked for me: (Note that "ubuntu" was the default user account name.)
```
sudo dnsmasq -q --enable-tftp --tftp-root=/home/ubuntu/voip_files_linux/tftp_root --address=/ls.tftp.vonage.net/vonage.net/voncp.com/192.168.1.99

```Sure enough, I got the following message after hooking up my voip box and plugging in the power. (It took about 2 minutes.) 
```
Aug 12 03:58:23 ubuntu dnsmasq[7289]: query[A] ls.tftp.vonage.net from 192.168.1.88
Aug 12 03:58:23 ubuntu dnsmasq[7289]: config ls.tftp.vonage.net is 192.168.1.99
Aug 12 03:58:23 ubuntu dnsmasq-tftp[7289]: cannot access /home/ubuntu/voip_files_linux/tftp_root/JFKeo3cOlW/spa0010211E99A1.xml: Permission denied
```Woohoo! Ok, now it was **very **important to make sure these folders and sub-files had full read/write permissions  for the *owner, group, and others* . Then I got the following message and all was well!
```
Aug 12 04:05:55 ubuntu dnsmasq[7430]: query[A] ls.tftp.vonage.net from 192.168.1.88
Aug 12 04:05:55 ubuntu dnsmasq[7430]: config ls.tftp.vonage.net is 192.168.1.99
Aug 12 04:05:55 ubuntu dnsmasq-tftp[7430]: sent  /home/ubuntu/voip_files_linux/tftp_root/JFKeo3cOlW/spa0010211E99A1.xml  to 192.168.1.88
```

---

