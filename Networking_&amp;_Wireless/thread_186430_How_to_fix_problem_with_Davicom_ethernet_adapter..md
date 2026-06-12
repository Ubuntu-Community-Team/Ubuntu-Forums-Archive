---
title: "How to fix problem with Davicom ethernet adapter."
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by h3h_timo on 2006-06-01
I noticed that there isn't a post for this yet, and many people have been having this problem, so i decided to make one.

The solution to fix this is relatively easy.  It's made up of only 2 steps.

First, you need to add dmfe to /etc/modules.  To do this you need to open up modules with gedit by typing the following code into a terminal.

```
sudo gedit /etc/modules
```

Then, you need to add "dmfe" to this, without the quotes.  Make sure you save.

Finally, you need to blacklist the tulip driver so it wont run at startup.  To do this you need to run the following in a terminal.

```
sudo gedit /etc/modprobe.d/blacklist
```

After this is opened, you need to add "blacklist tulip", without the quotations, somewhere in the file.  Then save.

After both of these steps have been completed, restart your system, and voila, you now magically have a working ethernet adapter.

I'm sorry if this is hard to understand, as it is my first post, and im fairly new to linux.

---

### Post by darmot7 on 2006-06-02
worked like a charm :D 

tyvm!

---

### Post by gozzerd on 2006-06-02
I did lsmod and found that both tulip and dmfe had been loaded. I googled about this and found a debian bug report about it. I did sudo ifdown eth1 to bring my interface down, then removed both tulip and dmfe with rmmod, put dmfe back in with modprobe then restarted the interface with ifup eth1.

Then I had internet again.

Then I blacklisted tulip like you mentioned. But I didn't explicitly put dmfe in modules, because it seemed to be getting loaded on its own already. All was good once I successfully rebooted on the 3rd try. 

my adaptor is a Davicom 9102 based PCI Fast Ethernet adaptor, which according to some things I read, is thought by some to work now with tulip. But it doesn't. dmfe is still the driver for it. At least on my machine, which is an old abit with an intel BX chipset.

I've fixed several things since doing an online upgrade to Dapper rc, but I still restart successfully less than half the time. Stalls most often while gdm is trying to load the login screen. Lots of intermittent weirdness though, like on a windows machine. never boots the same three times in a row.

---

### Post by TimJ on 2006-06-02
Thanks a million, this fixed my problem (well it has at present so fingers crossed). Now I'm back on Ubuntu.

---

### Post by InsanePenguin08 on 2006-06-02
Hot damn, internet's back up and running.
This is what I love about Linux!

---

### Post by ricnmar on 2006-06-02
h3h_timo,

First off; nice post - very nice!

OK, I just wonder where did you find this information?  I had this problem and found no help for it.  Where were you two days ago when I needed this info?  I ended up reinstalling thinking I had downloaded a bad file someplace.  Now I will run the update again and I can fix my NIC trouble!!

Thanks!
ricnmar

---

### Post by h3h_timo on 2006-06-02
Actually, i forget where i found it.  I worked for a couple of hours in IRC with a dude by the name of RandolphCarter, who was very helpful.  We couldnt figure it out, so i figured it was best just to downgrade.  Anyway, i decided to look for a few minutes and instantly i found that.  I would love to learn more so i can put more tutorials like this up.  Anyway, ricnmar, i just found out how to do that last night, so im in the same boat that you are.

-timo

---

### Post by Zombie process on 2006-06-03
Hi... had the same problem here. Thank you very much :D

---

### Post by CFMV on 2006-06-03
woah muchisimas gracias! my problem was kinda weird. My internet connection DSL worked for like 30secs everytime i resseted the modem and then nada. So i had to restart it like 1k times till i found this post.

MANY MANY THANKS!!!!

PS. Weird cases like this make me wonder if other distros have forums like this...<3 Ubuntuforums.org!!

---

### Post by daveg2 on 2006-06-03
H3h_timo, I had exactly the same problem with the same card.  My solution was the same.  Good job on describing the fix.

---

### Post by daveg2 on 2006-06-03
Woops, typed too fast with insuffient thought.  Both tulip and dfme were loading!  I couldn't ping the router.  Tried removing dfme and tulip failed after a short time.  Removed and blacklisted tulip for a solution.

---

### Post by jakenn-linux on 2006-06-03
[QUOTE=h3h_timo]I noticed that there isn't a post for this yet, and many people have been having this problem, so i decided to make one.

The solution to fix this is relatively easy.  It's made up of only 2 steps.

First, you need to add dmfe to /etc/modules.  To do this you need to open up modules with gedit by typing the following code into a terminal.

```
sudo gedit /etc/modules
```

Then, you need to add "dmfe" to this, without the quotes.  Make sure you save.

Finally, you need to blacklist the tulip driver so it wont run at startup.  To do this you need to run the following in a terminal.

```
sudo gedit /etc/modprobe.d/blacklist
```

After this is opened, you need to add "blacklist tulip", without the quotations, somewhere in the file.  Then save.

After both of these steps have been completed, restart your system, and voila, you now magically have a working ethernet adapter.

I'm sorry if this is hard to understand, as it is my first post, and im fairly new to linux.[/QUOTE]

Echo the comments about "where were you earlier with the solution".  I was also one that was dealing with this for the past 3 or so weeks.  I even installed (please, no one hit me) OpenSuSE 10.1 to see if my problem was just Ubuntu or any Linux.  Well after an easy install of SuSE I had the same problem.  Interent works if I unplug/plug in the cable but only for a few minutes (or until I ran into a large update download).  Since I hadn't been back on the forum to find your fix, I went the other night and bought a new NIC.  It installed and then I had to do a couple of settings in System/Admin/Network to enable and activate.  And its working just fine.  I'm almost tempted to put my Davidson back in and try your fix.  But I spent the money so I'll go with it.  I see that I have some downloads to get and this should be a real pleasure if I don't have to play "traffic cop".  Thanks for helping out so many others that were having the same problem.

---

### Post by h3h_timo on 2006-06-04
I'm glad that so many other people have been able to use this to fix their problem.  Its nice having a community in which everone loves to help each other out!!

---

### Post by abirdman on 2006-06-04
Thanks, sincerely. I just spent my whole weekend messing around with this-- and learned more than I ever wanted to know about ifconfig and route. The worst thing was the network worked from the LiveCD, but not after installation. I was booting into LiveCD, mounting the installed partition, and running diff against init.d and the /etc/network directories. I hope someone fixes this problem in the distribution, or it's just not going to pass the "can grandma install it?" test.

Thank you for the post with the actual solution. Ubuntu Dapper works like a champ now!

---

### Post by christian.convey on 2006-06-05
Thanks very much. That worked on my home computer, and I'll try it on my work computer today.  BTW, I've now mentioned this workaround in the bug report for this problem:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46822](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46822)

---

### Post by ricnmar on 2006-06-05
I too am sharing these instructions.  People on the Kubuntu forums are reporting the same symptoms.

Thanks again!
ricnmar

---

### Post by jakenn-linux on 2006-06-05
Hopefully someone will also be posting this over at the SuSE forums as I had the same problem with SuSE.  I installed it so I could see if it was a Ubuntu issue or if it was a linux.  It's a linux, but as we all know now it's the problem with the little "tulip" and the Davicom network card.

Sure has been a pleasure these past few days working on the Internet and not having to unplug/plug the cable to keep a connection.   Really enjoying Ubuntu.

Thanks all that had some part in helping us all resolve our problem.

---

### Post by Billi on 2006-06-05
I Thank You, the people who've had to work with my sleep deprived self thank you, my attention starved dog thanks you, and most of all my Mac addicted partner who bought a new faster router/modem that I couldn't use, ( and therefore he couldn't use) who threatened to banish me, my dog, and Linux to the garage forever, thanks you.

billi

p.s. oddly enough the unfixed file would work with my old netgear RP614v2 router and Alcatel dsl modem, but not the new netopia 3346 that my partner just bought

---

### Post by kaph on 2006-06-06
Thanks mate :) You are a gem!

---

### Post by devurandom on 2006-06-07
I add a "it-happened-to-me-too" post... just a few hours ago (Kubuntu 6.06 install on my laboratory machine, to replace an aging Debian Sarge).
Too bad I read this post on the forums just now, I had no way to figure it was the card's fault since it worked flawlessly with Knoppix and Debian Sarge... so I didn't look for it.

It was the second worst troubleshooting hell I ever had in nearly 3 years of Linux. Networking was up, then stopped to work after about 60-90 seconds, but it came back (for 60-90 seconds) by unplugging and replugging the network cable. I tried diagnostics with ifplugstatus, ethtools etc. I even browsed LKML. 

At last, suspecting an IRQ conflict, I wrote a line about tulip and irqs in the /etc/modules/options file... This didn't change the irq's :), but somehow probably b0rked tulip, so networking started perfectly.

Nice to know there's a known solution. Wheew. Next time I'll look in the ubuntuforums first :D

---

### Post by Dantrag on 2006-06-07
WOOT!!! You are a gentleman and a scholar for that fix! Love these forums!

---

### Post by Brighid on 2006-06-08
h3h_timo, thank you! =D> 

I had a problem with my Davicom adapter in Fedora Core 5, and after days of struggling finally solved it with a method similar to this one (had to change "tulip" to "dmfe" in a config file).  I made the move to Kubuntu Breezy not too long ago (FC was too technical for me) and had no troubles.  Updated to Dapper today and noticed shortly after installation that I was not connected!  I figured it was the same problem again, and it seems that it was.

Thanks for posting a quick and easy way to fix this.  I was afraid I was in for days of torture again. :rolleyes:

Cheers! :D

---

### Post by maudy on 2006-06-10
My ethernet is:
Silicon Integrated Systems [SiS]
SiS900 PCI Fast Ethernet
ASUSTeK Computer Inc.

And, too, DONT work!
Any tips?

thanks people!

---

### Post by shuffdog on 2006-06-10
Thanks a TON, timo, glad you're with us, I was having a bear of a time looking for help with a half-crippled driver.  Now Dapper Drake can finally be OURS!!!!

---

### Post by kumbakara on 2006-06-14
good fix. Worked for me also :D 
Tnx h3h_timo.

---

### Post by cleako on 2006-06-15
h3h_timo,

THANK YOU SO MUCH!

I was at the brink of looking for a different distro of Linux because I had the exact problem that so many others we're having.  Internet worked fine with the Desktop Live CD but after installing to the harddrive, it simpily stopped.

I now have internet thanks to your post, keep up the great work.

---

### Post by Noobie_Unbuntu on 2006-06-15
I am new to Unbuntu 6.06 I am having major problems with my inter net addapters! [COLOR="red"][COLOR="Navy"]**_Please Please help me_**[/COLOR][/COLOR]! I am at my wits end!!

I have tried two different working adapters that I had lying around:

1.  [COLOR="navy"][COLOR="Navy"] Intel Pro /100 ISA (TP) 651538 with i82556 chipset[/COLOR][/COLOR]

2.  [COLOR="red"][COLOR="Red"]SMC ultra 8416 ISA card[/COLOR][/COLOR]

Apprently there isn`t any drivers avalible to run The Intel Pro with Linux?????

The SMC card shows up under system devices as PNP1 , but is not visible under networking, the only device showed under networking is a fax modem PPP0???? which I removed from the PCI slot inside the case!

I have treid a "hot unplug replug" with the SMC ISA card, and tried using the dos program that came with the SMC driver to configure it, etc.. 

What I don`t understand is that the [COLOR="Red"]SMC card seems to register as PNP1, shouldn`t it be eth0, or eth1[/COLOR], being a Ethernet card for a cable interent connection?

---

### Post by whobutdrew on 2006-06-17
You can add another hit to your list.  This fixed me up perfectly.  Huge thanks!

---

### Post by divot on 2006-06-18
Worked for me too. Thank you. Thank you. Thank you.
Did I mention Thank You.

---

### Post by revision on 2006-06-18
Believe it or not, this might be a fix for other adapters also. I just installed Ubuntu 6.06 last night on the wife's machine. Was noticing this issue with a netgear NIC in the machine. Didn't give much thought to it, and went about our business. today i noticed it has been dropping a lot. I just did your fix and will see if it resolves the issue or not.

---

### Post by jice on 2006-06-19
This worked for me, and afaik I don't have a davicom adapter.  Mine is PRO200WL.

Thanks for the help!

(updated later... it is a davicom adapter... who knew :)

---

### Post by Tandarul on 2006-06-20
I can just thank you...

---

### Post by Hyrum on 2006-06-20
I downloaded Ubuntu and checked out. It worked great while it was running off the CD. I liked it a lot so I installed it. Right after it installed I checked for updates and my interned stoped working. I found this post and was able to fix the problem. It just took me a while to figure out what a terminal was. 

Thanks
Hyrum

---

### Post by xeonchen on 2006-06-22
It works on myethernet controller:

Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)

Thanks!

---

### Post by Mr Wolf on 2006-06-22
Dude, thanks for the fix. I couldn't figure out why my internet with 6.06 would work with the Live CD but not from my HD install. We will erect a statue of you in our village.


                             Ian

---

### Post by sweet_tooth on 2006-06-23
Just wanted to say how much this post helped me out. I had my problem fixed in a [COLOR="Red"]*flash*[/COLOR]!

Thanks.

---

### Post by Beltonius on 2006-06-25
First of all, thanks for posting this!

It has helped, but not entirely solved my problem. My Ubuntu machine can now ping other machines/devices on the network (and responds to their pings), as well as see the workgroup and the computers themselves and their shared folders.
Accessing things over the network is frustratingly slow; like minutes to open up a folder. I'm currently trying to get Rythmbox to read some music on a network share, we'll see how this goes. 

However, it still has no connection to the internet.

Network setup:
Internet -> DSL Modem -> Linksys WRT54GL router -> Linksys Router configured as switch -> Ubuntu machine (with a DEC Tulip etc PCI card)

I don't *think* I've done anything weird with the wired setup for the router; it's DHCP which generally works fine for everything. 

I commented out my addition of dmfe in /etc/modules and at the moment it's accessing the network. I will uncomment that and reboot and see if the network functions better.

Any other suggestions anyone has would be welcome!

---

### Post by TyeDye on 2006-07-03
Thanks for the fix!

---

### Post by wesm on 2006-07-04
thanks so much, worked as advertised.

---

### Post by ym4546 on 2006-07-06
[QUOTE=CFMV]woah muchisimas gracias! my problem was kinda weird. My internet connection DSL worked for like 30secs everytime i resseted the modem and then nada. So i had to restart it like 1k times till i found this post.

MANY MANY THANKS!!!!

PS. Weird cases like this make me wonder if other distros have forums like this...<3 Ubuntuforums.org!![/QUOTE]
i had the same problem, luckily i had an internet-working winxp computer nearby...

great post by the way h3h_timo....it was concise and solved the problem effectively

---

### Post by g.stuck on 2006-07-12
This solution worked for me.

I spent hours trying every other solution out there... disabling ipv6, modifying system files... but nothing seemed to work.

My internet would cut out after about 10 seconds.  Nothing could be done to bring it back, not a release/renew, not restarting the cable modem.

I have a CNet PRO200WL ethernet adapter.  It came with my Dell box.
If you have a similar hardware configuration, I would ex pect that this would work for you as well.  Note:  I still have IPv6 disabled from before trying this fix.  Not sure if that makes a difference, but I'm not going to bother turning it back on.

---

### Post by neilp85 on 2006-07-13
This is great, finally a solution that works. Spent several hours banging my head trying to figure this out.

---

### Post by monkieie on 2006-07-14
oh man I am A COMPLETE novice when it comes to linux. Had just installed Xubuntu on an old PC today which was working alright until *poof* - no ip traffic any more. I just googled for the prob and hey presto! 

Great solution!

It was fantastic to see how easy and quick it is to find solutions on the web. Try that with *other* OS :p 

:D :D

---

### Post by MindFul on 2006-07-22
Timo,

you are a five stars newbie for me now.

Thank you very much for your solution. 

Now I can use UBUNTU.

---

### Post by Manta on 2006-07-23
Yipee!!!  It worked for me too.  I have a Dell 8200 with a CNet card and couldn't get it working with Ubuntu 6.06.  It's working great now after following the steps.  Thanks timo...

---

### Post by Acuos on 2006-07-29
Thanks for the how to fix.  I have been stumped by this one.   Been trying out different Linux distros.  I had the same problem with SuSE SLED and Open versions, but was able to fix those by looking at the chipset.  Now to start configuring Ubuntu.  ^^  
 
I'm using the CNet PRO200WL by the way.  Yes, it's a Dell.

Now for XGL!

---

### Post by scotthershall on 2006-07-30
This fix also works for the 3Com 3c905C ethernet adaptor.  This is the built-in adaptor on my Dell Inspiron 4150.  

Now on to getting the wireless working...


These are great forums.


Thanks,

Scott

---

### Post by wilberfan on 2006-07-30
Holy crap--it *works*!   Nice goin!

:-)

---

### Post by blushores on 2006-08-02
> **gozzerd said:**
> I did lsmod and found that both tulip and dmfe had been loaded. I googled about this and found a debian bug report about it. I did sudo ifdown eth1 to bring my interface down, then removed both tulip and dmfe with rmmod, put dmfe back in with modprobe then restarted the interface with ifup eth1.

...

Hi, I have the same network card Davicom 9102 AF. I tried doing what h3h_timo and gozzerd suggested, but still it's not working. The funny thing is though, when I run Ubuntu from a live CD it works fine. I can access the internet, but not from the installation on the hard drive. I have changed the driver to dmfe from tulip and also blacklisted tulip. I am not sure what's the problem now? 

I am very new to Linux and Ubuntu, any help greatly appreciated. 

Thanks,
blueshores

---

### Post by blushores on 2006-08-04
I found a solution, Thanks to handy and stubadub. Please see my post at [http://www.ubuntuforums.org/showpost.php?p=1337130&postcount=9]("http://www.ubuntuforums.org/showpost.php?p=1337130&postcount=9")

---

### Post by crono on 2006-08-20
I did the changes at modules and blacklist, as suggested, but Kubuntu 6.06 now connect just a few minutes. 
No way to get a new connection until next reboot. I tried ifdown/ifup, dhclient, static IP and DHCP. What i get is a "no lease" message. If i try to ping the router the answer is that the network is inaccesible. 

Is there anyone who got (and, hopefully, resolved :) ) the same problem?  

any help will be invaluable to me.
Thanks

---

### Post by leargaf on 2006-08-21
Same here. Excelent post!
Thanks

---

### Post by David Corrales on 2006-08-22
Awesome, thanks :D

---

### Post by Mikeyboy1 on 2006-08-26
I've tried typing sudo gedit /etc/modules and I get an error message saying 'no such command'. What am I doing wrong?!

---

### Post by Red Knuckles on 2006-09-16
Thanks, h3h_timo your 1st post in this thread worked for me.

---

### Post by feTzu on 2006-09-26
I Love you, thanks a f***g lot :D 

Now let's go for part two, get that damn wireless card working :(

---

### Post by RArocks12 on 2007-01-23
This solution worked great for me the first time I tried it.  But I then shut down my computer for the night and on several occasions I have tried to connect to the internet again but it seems to have stopped working.  I took away the added lines and then put them back in again but its not working anymore.  Is anyone else having this problem?

---

### Post by ayed on 2007-02-14
I am sorry...me stupid (blush) where do I put the dmfe?

---

### Post by Red Knuckles on 2007-02-15
> **ayed said:**
> I am sorry...me stupid (blush) where do I put the dmfe?

sudo kwrite /etc/modules

See the very 1st post in this thread.
):P [-X

---

### Post by kroenecker on 2007-06-16
Thank you SO MUCH for posting this article.  I just install Feisty onto my old Averatec and it was freezing up really really badly.  Fortunately, by blacklisting rt2500 everything works great!  No more slowdown!

---

### Post by eqo314 on 2007-08-17
My issue is that the internet worked for a good week after I first built my ubuntu box.  The internet stopped working on Wednesday night and worked again on THursday morning but stopped working that night.  I checked the network monitor, looks like i get some data received, but still can't connect to google.  

I'm using versiion 7.04 on a new machine, my ethernet controller is integrated into the motherboard. My motherboard is an  ASUS M2NPV-VM Socket.  I wonder if this fix will work on my machine .  We'll see tonite.  

Overall, my experience with ubuntu has been overwhelmingly positive.

---

### Post by eqo314 on 2007-08-19
i got home friday and brought home my work laptop.   i turned on my desktop ready to figure out why the internet wasn't working before and as the pc was able to connect now.

---

### Post by crono on 2007-09-02
i did the two step changes recommended (dmfe & blacklist tulip) but my connection still goes down after a random amount of time: sometimes after 50 minutes other after 5 hours.
Any other suggestion ?

---

### Post by zak44 on 2007-09-18
Mahalo! 

Strange thing to me was that I could access the net when I loaded the live CD, but couldn't after installing on the same PC from the live CD -- go figure ?

Anyway, works now!

---

### Post by funzy on 2007-09-24
I use DM9601 usb ethernet card of Davicom.
when i lsusb:
Bus 001 Device 004: ID 0a46:9601 Davicom Semiconductor, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

when i lsmod:
Module                  Size  Used by
i915                   25793  2 
drm                    78037  3 i915
autofs4                24645  2 
hidp                   26433  2 
rfcomm                 43481  0 
l2cap                  30145  10 hidp,rfcomm
bluetooth              57125  5 hidp,rfcomm,l2cap
sunrpc                159133  1 
nf_conntrack_ftp       13761  0 
nf_conntrack_netbios_ns     7105  0 
xt_state                6593  2 
iptable_filter          6977  1 
ipt_MASQUERADE          7745  1 
iptable_nat            11461  1 
nf_nat                 22125  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      15049  4 iptable_nat
nf_conntrack           61001  7 nf_conntrack_ftp,nf_conntrack_netbios_ns,xt_state,ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink              10841  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
ip_tables              16389  2 iptable_filter,iptable_nat
xt_tcpudp               7233  14 
ip6t_REJECT             9537  2 
ip6table_filter         6849  1 
ip6_tables             17541  1 ip6table_filter
x_tables               18757  7 xt_state,ipt_MASQUERADE,iptable_nat,ip_tables,xt_tcpudp,ip6t_REJECT,ip6_tables
dm_multipath           21705  0 
video                  21065  0 
sbs                    19173  0 
i2c_ec                  9281  1 sbs
button                 12113  0 
dock                   13669  0 
battery                14149  0 
ac                      9413  0 
ipv6                  276673  25 ip6t_REJECT
parport_pc             29797  0 
lp                     15977  0 
parport                38025  2 parport_pc,lp
loop                   19785  0 
dm9601                 13505  0 
usbnet                 21961  1 dm9601
mii                     9409  2 dm9601,usbnet
fw_ohci                19649  0 
snd_hda_intel          24281  5 
snd_hda_codec         202689  1 snd_hda_intel
snd_seq_dummy           7877  0 
snd_seq_oss            33345  0 
fw_core                42625  1 fw_ohci
sdhci                  21069  0 
mmc_core               30661  1 sdhci
snd_seq_midi_event     11073  1 snd_seq_oss
snd_seq                50353  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
arc4                    6209  2 
ecb                     7489  2 
blkcipher              10181  1 ecb
rc80211_simple          8257  1 
bcm43xx_mac80211      397857  0 
ssb                    35012  1 bcm43xx_mac80211
serio_raw              10821  0 
pcspkr                  7105  0 
mac80211              136005  2 rc80211_simple,bcm43xx_mac80211
i2c_i801               12241  0 
ata_generic            12229  0 
iTCO_wdt               14693  0 
tg3                   104517  0 
iTCO_vendor_support     7877  1 iTCO_wdt
i2c_core               24641  2 i2c_ec,i2c_i801
snd_seq_device         11852  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            43489  0 
snd_mixer_oss          19393  2 snd_pcm_oss
cfg80211               12105  1 mac80211
snd_pcm                74565  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              24773  3 snd_seq,snd_pcm
snd                    53189  15 snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11553  2 snd
snd_page_alloc         13769  2 snd_hda_intel,snd_pcm
sr_mod                 20197  0 
joydev                 13441  0 
cdrom                  37217  1 sr_mod
sg                     37213  0 
dm_snapshot            20709  0 
dm_zero                 6209  0 
dm_mirror              24277  0 
dm_mod                 57229  9 dm_multipath,dm_snapshot,dm_zero,dm_mirror
ata_piix               18757  0 
ahci                   24133  2 
libata                115417  3 ata_generic,ata_piix,ahci
sd_mod                 23873  3 
scsi_mod              137549  4 sr_mod,sg,libata,sd_mod
ext3                  125385  2 
jbd                    59881  1 ext3
mbcache                12357  1 ext3
ehci_hcd               35405  0 
ohci_hcd               23749  0 
uhci_hcd               26833  0 

So what should i do to make my card work. It seem worked but when i acces a website the browser say "waiting" forever and then i can not ping any host.
Thanks

---

### Post by claudio4j on 2008-02-07
I have had this issue, but could not solve it yet.

I guess it is related to the packet size, because some small web pages and samba shares (with short number of files) its possible to use, otherwise there are lost packets.

[http://ubuntuforums.org/showthread.php?t=688314](http://ubuntuforums.org/showthread.php?t=688314)

---

### Post by claudio4j on 2008-02-07
I have solved the issue related to my problem 

[http://ubuntuforums.org/showthread.php?t=688314](http://ubuntuforums.org/showthread.php?t=688314)

---

### Post by cdardano on 2008-03-03
Hi h3h_timo!!!

Your post solve my problem, after 2 days looking for the fix.

Thanks!!!!!!!!!!!!!!!!!!!!

---

### Post by DarkGKnight on 2008-05-21
The steps in this post don't work for me. On Ubuntu 6.06LTS, my Davicom adapter worked when I disabled dmfe, and enabled tulip. However, now that I'm running Hardy, blacklisting dmfe does not work. The module is still loaded at boot time. When I 'rmmod dmfe' and 'modprobe tulip', the interface is not brought back up. On Hardy, dmfe is the only module that makes the interface come up, however I get the 'Tx timeout - resetting' error described in [another thread]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=547289"). The pci=noacpi fix does not work for me. I want to know if it is possible to stop udev from associating dmfe with my card, and force it to use tulip.

My /etc/udev/rules.d/70-persistent-net.rules has the following:
>  # PCI device 0x1282:0x9102 (dmfe)

---

### Post by SantiSolari on 2008-06-10
OMG!!! This solved mi problem like a charm!

---

