---
title: "All networking stopped"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by Phil Binner on 2011-07-09
I have a more or less annual attempt to get Ubuntu working, but it always fails on networking. Usually I have tried on old machines built of left over bits, but this time I tried version 11.04 on a fairly modern Acer Aspire 7520 laptop. I used a wired connection during setup and then set up the wireless. All was fine and easy, and I actually imagined that I might finally escape from Microsoft. Then a week later the networking stopped working on both wired and wireless. My windows machines and android phone connect wirelessly. My Windows desktop connects using the same ethernet cable. I tried re-installing Ubuntu from the original disk, but now I can't even get a wired connection during setup, so it seems to be something Ubuntu has done to the hardware settings (that is a surmise).

There seem to be a lot of us with versions of this problem. Help please.

---

### Post by Phil Binner on 2011-07-09
I should have said, the wired connection seems to be working fine. There is a solid green light and a flashing amber one, and it works for a different windows machine. The computer can see both my wireless networks, but after trying to connect for some time it fails on authorisation. Nothing has changed on passwords, etc., since it did work.

---

### Post by aldee96 on 2011-07-09
bump

---

### Post by Phil Binner on 2011-07-09
Hi. I'm not a regular forum user. What does Bump mean.

---

### Post by nm_geo on 2011-07-09
> **Phil Binner said:**
> Hi. I'm not a regular forum user. What does Bump mean.
He brought your message up to top..
Don't know why..

go to terminal do these and give us results

```
lspci -nn

``````
rfkill list all
``````
sudo lshw -C network
```

---

### Post by chili555 on 2011-07-09
> **Phil Binner said:**
> Hi. I'm not a regular forum user. What does Bump mean.aldee96 may or may not have the same problem and is interested in the answer.

---

### Post by SoFl W on 2011-07-09
> **Phil Binner said:**
> Hi. I'm not a regular forum user. What does Bump mean.

When a new message appears in a forum it moves to the top of the "new posts" list.  Adding a simple message such as "bump" will move the message to the top so more people see it.
However it is advised to wait at least 24 hours to "bump" a message if no one has responded to it.  Sometimes it is because no one knows the answer.  Everyone thinks their problem is urgent and important, frequent bumping only makes you look like an impatient ice hole.

---

### Post by Phil Binner on 2011-07-10
OK. Thanks. I may get into this slowly.

Here are the outputs requested from terminal commands.



bigbin@Middlebin-Ubuntu:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation C67 [GeForce 7000M / nForce 610M] [10de:0533] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:04.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
01:04.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
01:04.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
01:04.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)


bigbin@Middlebin-Ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

bigbin@Middlebin-Ubuntu:~$ sudo lshw -C network
[sudo] password for bigbin: 
PCI (sysfs)

---

### Post by chili555 on 2011-07-10
nm_geo has not yet appeared, I hope I will not step on his toes by helping for a few moments. He will want to see:```
sudo modprobe ath5k
iwconfig
sudo iwlist wlan0 scan
```Network Manager will disallow a wireless connection as long as you have wired; please detach the ethernet cable as we troubleshoot.

Are you aware that, unlike Windows, Network Manager requires that you click on its icon to see and select your trusted network and not any old spammer/scammer/hacker's unsafe network? Have you tried it? Do you see any networks?

---

### Post by Phil Binner on 2011-07-10
Hi

While I have been trying to sort this the ethernet cable has gone in and out. I have not been able to establish either a wired or wireless connection. Currently it is out.

There may be a bit of a clue in the output below, in that the second of your commands - iwconfig - finds 'Livebox-1E45' but doesn't find anything about 'DraTek'. I have just descovered that the windows machines are having problems connecting to 'Livebox-1E45' at the moment. The network all the other machines use is 'DraTek'. The scan saw 'DraTek'

I tried to paste the output into here, but for some reason the system thinks it includes 16 images, which it won't allow. A .doc file is attached instead.

---

### Post by chili555 on 2011-07-10
> Cell 03 - Address: 00:18:E7:5A:4B:F5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key: on
                    ESSID:"Livebox-1E45"This is from the scan results. Notice the Quality is 36/70. Your wireless will have difficulty attaching to a weak signal. Is there any signal strength setting in the router? Is it set to 100% Please see attached.

Is the router defective?

You will have better luck pasting a .txt rather than a .doc.

---

### Post by Phil Binner on 2011-07-11
Sorry about the .doc instead of text. The reason is that my Ubuntu machine has no network of any kind. I'm having to paste the output into a .rtf file and copy it onto a stick. Then I can open it on a windows machine that has networking. If I open it as a text document it comes out garbled and unreadable, so I opened it in word, sorted the format to get rid of all the blank lines, then tried to cut and paste the text. For some reason the Forum decided that contained 16 images, where the limit is 8. As far as I'm concerned there are no images, but hey, what do I know. The only format I have which I can attach to a post is .doc . This is less than ideal. I really need my network problems solved.

Less of that. The weak signal you see is from Livebox-1E45. All this router does is supplies free voip calls, and an internet feed to the other router - DrayTek:

Cell 02 - Address: 00:50:7F:60:B0:38                     Channel:6                     
Frequency:2.437 GHz (Channel 6)                     
Quality=64/70  
Signal level=-46 dBm                      
Encryption key:on
ESSID:"DrayTek" 

The wired connection (when it's plugged in - not now) goes to DrayTek. When I first installed Ubuntu I immediately connected to Draytek wirelessly, with no problem, and I was connected for about a week before everything suddenly stopped working. It's a wireless N Gigabit router, which I need to cover an old stone house with very thick walls. Nothing has changed on DrayTek since this happened, and all our windows machines and my Android phone connect to it with no problems.

There is a connection to DrayTek in the network manager, and I've checked the settings to make sure they're still OK.

I've just found out what the images are. The forum text interpreter thinks ":" followed by "o" is a smiley. I don't want to appear paranoid, but are they out to get me or what.

---

### Post by chili555 on 2011-07-11
I have no problem with .doc; I was merely explaining why your copy and paste didn't work. Feel free to continue as before. You might be able to get around this:> I've just found out what the images are. The forum text interpreter thinks ":" followed by "o" is a smiley.You could try checking off the box to disable smileys in the reply area or manually change Encryption key:on to Encryption key:  on.

Is there a listing in Network Manager for Livebox-1E45, the access point you wish to *NOT* connect to? Except you *DO* want to connect to it to make calls?? I wonder if the underlying problem is that NM is roaming between the APs and never settles on one. You might try checking 'Connect automatically' at DrayTek and making sure it is unchecked in Livebox-1E45. Please see attached.

---

### Post by Phil Binner on 2011-07-11
Hi again.

If I go into "Edit Connections" in Network manager, the only connection in the Wireless tab is DrayTek. I must have deleted the entry for Livebox yesterday. It doesn't make any difference; still won't connect. I haven't tried plugging the wire back in, but I believe the problem with getting a wired connection started at the same time as the wireless problem. That sounds to me as if they're related.

To try to avoid confusion, I only want to connect to Livebox to do maintenance on it, and I do that with a wire to my Windows netbook (very rarely). The way the Voip works is that you plug a phone into the livebox and use it like any other phone. I actually take the output from that and back feed it into line 1 on my telephone switch, so I get a 2 line system around my house. The point of this is that I never have to connect a computer to it wirelessly, though I should be able to, and I used to be able to. I probably could now if I reset it to factory settings. It's a primitive piece of kit, and I only have it at all because my ISP can't use the Voip from any other router, and free national and international calls is a valuable commodity. The only impact it has on the computer network is that there is an ethernet cable from it to the DrayTek Vigor 2710Vn router that runs the network. That cable supplies internet.

Actually, having explained all this, there is a distinct possibility that my problems with Ubuntu could have started at the same time as the Livebox lost it's wireless connectivity. The internet comes through a wire, however, and only the Ubuntu machine is affected. Could that be relevant.

---

### Post by Phil Binner on 2011-07-11
I have just tried something else. I found an unsecured router (probably across the road) and connected to it. It's very weak, but it connects.

So my problems may be with the two routers I have. The Livebox I know has a problem, so that is probably a red herring. Both the wired and wireless connections go through the DrayTek router, so could Ubuntu have developed a problem with it. There is a firewall capability on the router, but I've never set it up because I don't understand it. Could DrayTek be rejecting Ubuntu, rather than the other way round. Is there any way I could find out.

---

### Post by chili555 on 2011-07-11
> I haven't tried plugging the wire back in, but I believe the problem with getting a wired connection started at the same time as the wireless problem. That sounds to me as if they're related.I doubt it. I have been connected wired and wireless, but never at the same time, to the same router with no issues. NM is designed to disallow a wireless connection if wired is available and does so pretty well. > The point of this is that I never have to connect a computer to it wirelessly,Is it possible to remove its wireless capability? Please see attached.> If I go into "Edit Connections" in Network manager, the only connection in the Wireless tab is DrayTek. I must have deleted the entry for Livebox yesterday. It doesn't make any difference; still won't connect.When you click the NM icon and see DrayTek as an available network, does it ask for the encryption key? Does it try? What does syslog say afterwards?```
sudo cat /var/log/syslog | grep etwork | tail -n20 > log.rtf
```Transfer log.rtf and post it here.

---

### Post by Phil Binner on 2011-07-11
Hi

I guess you're a few hours behind me. What time is it there. I'm going to have to leave for a little while but I hope to be able to carry this on later, if you're still around. I'm really appreciating this.

When I try to connect to DrayTek for the first time it asks for the password. Once it has established that it doesn't ask again, unless I go into NM and delete the wireless connection.

I tried running your command, but nothing seemed to happen. I then noticed that you say "grep etwork", so I changed that to "grep network" instead, and still nothing seemed to happen. I searched for a file called log.rtf, but nothing was found.

The good news is that I have a wireless connection to livebox now. I took the computer downstairs and sat next to the livebox router, then re-booted livebox and got a connection. Once established it has held, so I'm working on the Ubuntu machine. One red herring gutted. I'll just not turn this off. I'm now suspecting that the problem is one between DrayTek and Ubuntu.

I'm not sure as to the full sequence of events you want me to go through, and how to get the log.rtf file. Do you want me to delete the entry for DrayTek in the NM then re-establish it before running the log.

When I ask it to connect to DrayTek it tries but fails.

---

### Post by chili555 on 2011-07-11
It is 12:20pm here, almost time for PB&J. > When I ask it to connect to DrayTek it tries but fails.That's what I want to see the result of in syslog.

The grep etwork was intended to show all instances of NetworkManager or network. It is a crude equivalent of grep -i network. The fact that is was empty suggests that syslog was archived as syslog.1 and a new one started. NM had not yet been active when you ran the command. Please delete all networks in NM > Edit Connections > Wireless and save. With the ethernet detached, try to connect again and try:```
sudo cat /var/log/syslog | grep etwork | tail -n20 > log.rtf
```The file log.rtf will be in your user directory. Drag and drop it to a USB key and transfer it and post it here, Hopefully, we can see a reason your wireless won't fall in love and marry DrayTek.

---

### Post by Phil Binner on 2011-07-11
I don't know what is happening, but I managed to connect to Livebox-1E45 and then had to go out. When I came back the computer had connected itself to DrayTek.  I read your post, then disconnected DrayTek and deleted the connections. Following that I tried connecting to both DrayTek and Livebox, several times, but I was ignored each time. No attempt to ask for a password; no attempt to connect; nothing. So I went back into NM and added a connection for DrayTek manually. I attempted to connect to that, and still got nothing.  

So then I re-booted the computer, and when it came on it connected to DrayTek without a second thought.  What the #### is happening.

The output from your command is below.

Jul 11 18:06:16 Middlebin-Ubuntu NetworkManager[571]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info>   address 192.168.1.12
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info>   prefix 24 (255.255.255.0)
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info>   gateway 192.168.1.1
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info>   nameserver '192.168.1.1'
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: nm_ip4_config_add_nameserver: assertion `nameserver != s' failed
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info>   nameserver '192.168.1.1'
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info>   domain name 'home'
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info> Scheduling stage 5
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info> Done scheduling stage 5
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 11 18:06:19 Middlebin-Ubuntu NetworkManager[571]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 11 18:06:20 Middlebin-Ubuntu NetworkManager[571]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Jul 11 18:06:20 Middlebin-Ubuntu NetworkManager[571]: <info> Policy set 'Wireless connection 1' (wlan0) as default for IPv4 routing and DNS.
Jul 11 18:06:20 Middlebin-Ubuntu NetworkManager[571]: <info> Activation (wlan0) successful, device activated.
Jul 11 18:06:20 Middlebin-Ubuntu NetworkManager[571]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.

---

### Post by Phil Binner on 2011-07-11
I just read the log above, wondering if I could make any sense of it. One strange thing struck me - the ip address of Livebox-1E45 is 192.168.1.1 . The address of DrayTek is 192.168.1.101 .

Perhaps that's not relevant.

---

### Post by chili555 on 2011-07-11
It looks like it connected perfectly to x.1.1. I am puzzled by this:> Policy set [COLOR="Red"]'Wireless connection 1'[/COLOR] (wlan0) as default for IPv4 routing and DNS.Here is what my computer says:> <info> Policy set [COLOR="Red"]'Auto GBR1'[/COLOR] (eth1) as default for IPv4 routing and DNS.GBR1 is the name of my network. I am puzzled by why yours says neither DrayTek or LiveBox.

Unfortunately, we have a log of a great connection to the wrong network and not a log of a failure to connect to the right network.

I'll be away for a while. See you later.....

---

### Post by chili555 on 2011-07-11
Is it possible to get a log of an unsuccessful attempt to connect to DrayTek?

---

### Post by Phil Binner on 2011-07-12
I have more new information. 

First, Wireless connection 1 is Draytek. It's the name the connection got given when I put it in manually, just prior to the re-boot which got this working. I guess the address line 192.168.1.1 in the log is another red herring. It's just that I don't understand what I'm reading.

Second, the log was taken right after the re-boot, when everything was working properly. If the log starts afresh with the new session then it wouldn't show anything abnormal. 

Third, I actually have a second Ubuntu machine, a desktop built out of old bits and pieces. I have tried this several times before, and it's always failed for one reason or another. The current version I have now would never connect either wired or wireless. Currently the wireless card is still in, but wireless networking is turned off.  It's wired connection goes to DrayTek. When the reasonably new laptop started working yesterday, I tried the desktop again, and lo and behold it connected. Strangely, the internet works, but it can't download updates. That's probably a different story, but it seems likely to me that the other things are related.

How I see it is, 

1.  Livebox is a poor piece of kit which goes wrong fairly often. I have to keep it because it saves me a lot of money on my phone bills. All it is supposed to do is provide a second phone line to the phone switch, and provide internet to DrayTek.
2.  DrayTek should provide the network, regardless of whether or not it has internet. If it has internet it should pass it on.
3.  There is a possible state for Livebox where it provides internet but not wireless networking. When it is in this state The windows machines can log onto Draytek and get internet, but the Ubuntu machines can't. I know this because I used the Windows netbook with Livebox yesterday, and after I had got it sorted out both Ubuntu machines could connect to DrayTek.

What I could try later is powering down Livebox and trying to connect to DrayTek without any internet feed. Unfortunately that will take out my phone system, so I'll have to pick the time. Other than that, I can't think of a way of putting Livebox into it's half failed state to get the log you have requested.

In the meantime, what is the difference between Windows and Ubuntu that would let one connect but not the other.  Answers on a postcard to .........

---

### Post by Phil Binner on 2011-07-12
OK. Livebox has gone wrong again - no internet for anybody. I re-booted it and the windows machines got connection to DrayTek back, with internet, but the Ubuntu machines didn't. Currently they can't connect, though I could probably sort that by taking the netbook down to it and connecting wired.

Anyway, here is the log imediately following a failed connection attempt.


Jul 12 18:03:53 Middlebin-Ubuntu NetworkManager[576]: <info> Config: set interface ap_scan to 1
Jul 12 18:03:53 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 12 18:03:54 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 12 18:04:04 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jul 12 18:04:04 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 12 18:04:08 Middlebin-Ubuntu NetworkManager[576]: <warn> (wlan0): link timed out.
Jul 12 18:04:22 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 12 18:04:32 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jul 12 18:04:32 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 12 18:04:33 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 12 18:04:43 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jul 12 18:04:43 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 12 18:04:44 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 12 18:04:53 Middlebin-Ubuntu NetworkManager[576]: <warn> Activation (wlan0/wireless): association took too long.
Jul 12 18:04:53 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): device state change: 5 -> 9 (reason 7)
Jul 12 18:04:53 Middlebin-Ubuntu NetworkManager[576]: <warn> Activation (wlan0) failed for access point (DrayTek)
Jul 12 18:04:53 Middlebin-Ubuntu NetworkManager[576]: <info> Marking connection 'Wireless connection 1' invalid.
Jul 12 18:04:53 Middlebin-Ubuntu NetworkManager[576]: <warn> Activation (wlan0) failed.
Jul 12 18:04:53 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jul 12 18:04:53 Middlebin-Ubuntu NetworkManager[576]: <info> (wlan0): deactivating device (reason: 0).

---

### Post by chili555 on 2011-07-12
> Currently they can't connect, though I could probably sort that by taking the netbook down to it and connecting wired.I don't quite understand this. What do you do to DrayTek that makes the Ubuntu machines able to connect where they couldn't previously?

---

### Post by Phil Binner on 2011-07-12
I don't need to do anything to Draytek. I have discovered, through the course of this conversation, that I can fix it through intervention with Livebox. Since we last spoke livebox has had a fairly major failure, the first obvious one for about a month, and it's been taken back to factory settings. All is well now. For a while I lost all phone and all internet, but that's sorted for Windows and Ubuntu.

From what I understood of the log I posted, all it showed was that it tried to connect then timed out. This is clearly not a failure of Ubuntu, though I need to understand what the difference between Ubuntu and windows is when they are making contact. In this context Windows seems to be able to keep contact when Ubuntu can't. I suspect that understanding the problem and tweeking the linux system would sort that. 

What I'm thinking now is that the relationship between Draytek and Livebox is not just the supply of internet but the supply of ADSL. I wish I actually knew, but I'm guessing that ADSL is the wrapper that internet is provided in, and that the reason DrayTek is failing is that it is an ADSL router that is being provided with faulty ADSL. Unfortunately it's only partially faulty, most of the time, so it keeps up a faulty service.

I hope you are still interested here. It's clear the culprit is banged to rights, and it's not Ubuntu. However, I'm stuck with Livebox, at least until I want to put another £40/month on my phone bill, and if we could find out what the difference is between the way Ubuntu connects and the way Windows connects we would probably sort it.

PS when I cleared Livebox back to factory settings and re-set it up, I turned of wireless networking. We'll see if that has any effect.

Over to you.

---

### Post by chili555 on 2011-07-12
I'm always interested. In my ten years plus in Linux, I almost every day learn something new and I enjoy it immensely. What is fascinating to me in Linux is that in ten years I have come to believe that I have learned about 5% of what I wish I knew and about 1% of what there is to learn. However, as much as I'd like to, I can't answer every question. Some people go away dissatisfied.

I am not sure I understand much about how Windows connects except it's less secure than Ubuntu. For example, if you walk in to the cyber cafe with an unencrypted wireless network and start your Windows computer, I understand it will connect. In Ubuntu, you must select the network; it is up to you to click it and select a trusted network. Once you have connected to it and selected 'Connect Automatically' it will do so as long as the network name and encryption are unchanged. 

I have not used Windows, except to set up my Harmony remote, in many years.

I am interested in the ADSL part of the puzzle. Is it like DSL here in the colonies? Does it arrive on the telephone line? Do you provide a user name and password to the DSL provider, also known as internet service provider? In my DSL system, those are written in the administration pages of the wireless router provided by the ISP. Therefor, those details are not required to be configured in each computer. My computer sees an ordinary wireless connection where I merely need to supply the correct WPA2 password.

Is that how ADSL works over there in the Mother Country?

The log shows exactly what you thought; it showed was that it tried to connect then timed out. Unfortunately, it doesn't show a fixable reason. It's my favorite kind of problem; everything looks perfect and it ought to work but it just won't. It's the stuff of nightmares.

---

### Post by Phil Binner on 2011-07-13
Well, glad you're having fun. Yes, ADSL is as you describe. I consider myself to be a reasonably intelligent, reasonably computer literate, end user, and not at all technically oriented, but having just looked it up I can tell you that ADSL stands for Asymmetric Digital Subscribers Line, and is one common type of DSL. There are others. Basically it's what we use in the UK for normal purposes. I suspect it's the same in the US, but I can't confirm that. It comes into your house in a normal telephone line, but you then have to attach a splitter to separate out the digital and analogue sections of the signal. As you say, all the important stuff is stored in the router, and you just have to worry about the access code.

If you're interested you could look at this article [http://www.buzzle.com/articles/difference-between-dsl-and-adsl.html](http://www.buzzle.com/articles/difference-between-dsl-and-adsl.html)

I can now confirm that Livebox is the problem. My system has the telephone line coming into the house and connecting to livebox. Since you can't have 2 routers on one line, I have an Ethernet connection from Livebox to DrayTek to shunt the ADSL, and therby hangs the problem. Unfortunately, as I said, I need DrayTek to provide the power and Livebox to provide the second line. I put in a request to my ISP yesterday to look into using the Voip capability on DrayTek so I can get rid of Livebox alltogether. I'm sure they could do it, they should only need it's MAC address, but they're lazy. I'll await the outcome.

Unfortunately when I started the computer this morning access had stopped again. This time it only took a simple Livebox reboot to sort it, but it doesn't bode well. If it persists I may have to abandon my Ubuntu experiment yet again, even though we've established it's innocence.

A longer term problem is that I'm on the verge of buying a server. The one I'm considering is an HP Prolient N36L, which comes with Microsoft Windows Server and Red Hat enterprise Linux. This would be set to be accessible remotely. I'm worried about using Windows Server because I don't trust those devil worshippers as far as I can smell them (and I have no reason to believe they don't wash), specifically, I worry that they'll try to restrict access to other windows machines only, and who, in the real world, uses windows for servers. But if I opt for Red Hat Linux, will that also keep falling off the network. 

Or, if I do get a server, do I still operate the network in the same way. If I don't I'm likely to loose my second line anyway.

Still, I think I can mark this streem as solved now. I'll just leave it for a short while to see if anyone has any insights to my problem.

Thanks for all your help.

---

