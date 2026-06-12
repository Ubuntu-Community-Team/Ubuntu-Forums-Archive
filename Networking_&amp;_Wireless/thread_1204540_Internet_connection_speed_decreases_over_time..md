---
title: "Internet connection speed decreases over time."
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by Spike1158 on 2009-07-04
I decided to post my headache of a problem on the great Ubuntu forum's because of my new loved OS for the past 3 weeks, Ubuntu. And 1st off this is not an Ubuntu problem, because its been going on for roughly 2 months now.

As the title says, my connection speed decreases over time. Verizon isp, paying for a 3Mb connection. Westell 6100 EP90-610015 modem and a Linksys BEFW11S4 V4 router, main computer running Vista, my wireless computer running XP/Ubuntu dual boot.

When my connection is normal, i can go to my Modem configuration page, typing in the IP address in firefox, 192.168.1.1 and it shows DSL Connect Rate 3300Kbit/s down, and 750ish Kbit/s up. As the day goes by my connection goes down. like right now im at 1056Kbit/s down and 736Kbit/s up. Ive been leaving the modem and router off at night, and when i turn everything on in the morning, speeds are normal. Sometimes in a few hours it goes down or sometimes its ok for most of the day, but eventually it drops, alot and quick. When it does i turn everything off for about 30 minutes, then its back to normal for a few hours. I get the same results on both computers, and it dosnt matter if im on Xp or ubuntu, it happends. Ive seen it drop all the way to the 200Kbit/s range and it feels like AOL dial up days :(

Ive done google searches on the westell 6100 modem and it seems very problematic, but never found anything that resembles my problem. Ive done searches on my specific modem/router combo, nothing. Ive reset both modem and router, then reconfigured it to work..modem has to be in routed bridge mode so it works with a router instead of as a router, but still nothing.

So you guys are my 1st to last resort, which is call Verizon and go through the whole "sir is the ethernet cable in the ethernet port" process. ANY help/suggestions are greatly appreciated and sorry if this belongs in a different thread, might end up going to the hardware thread because of my pos modem which i think it is!! and let me know if u need any other info to help me figure this out.

---

### Post by Spike1158 on 2009-07-05
bump, please help!!

---

### Post by philcamlin on 2009-07-05
how wmy people are connected to the network at the normal apeed and slow speed

and it all depends how meny people are torrenting etc at the time in your area...

at my old house in my area there were alot of torrenters and the dl would be slow at night but when they stopped it would be really fast :popcorn:

---

### Post by lisati on 2009-07-05
Is anyone sneaking on and "borrowing" your wireless connection?

---

### Post by Spike1158 on 2009-07-05
There's only 2 computers connected to the network...i have access logs on my router enabled and i watched them for a few days, and nothing suspicious pointing to someone sneaking connection, but thats the only way i know how to see who is connected to my network, that and the lights on my router lol...i do have it WEP secured and change the password once a month which is a good habbit.

As for the different speeds at internet "rush hour" in my area, time of day/night dosn't seem to be a problem with my speed decreasing...if it was that, my connection speed would go back up during non rush hour..but it dosnt, once it goes down, it stays down untill i physically turn my modem off for a while. 

Ive been monitoring it today, and so far ive stayed at 1056Kbits/s connection except when i turned everything on this morning at it was at 3300. it took about 3hrs to decrease to that speed this morning, and there was no heavy internet use either, just checking mail, ebay surfing...the normal. no crazy 4gb DL's.

and ty so far, any ideas/suggestions are extremely helpfull, because a 20lb sledge to that modem is sounding really fun at this point.

---

### Post by lisati on 2009-07-05
> **Spike1158 said:**
> i do have it WEP secured and change the password once a month which is a good habbit.
If your hardware can handle it, it might be a good idea to change to WPA encryption as an extra precaution, because it's supposedly more secure.

---

### Post by Spike1158 on 2009-07-05
> **lisati said:**
> If your hardware can handle it, it might be a good idea to change to WPA encryption as an extra precaution, because it's supposedly more secure.

sadly no, the only option in my router config page is WEP...i had a new router that was set up WPA encrypted but i kinda bricked it lol. tried flashing it with a custom firmware and it went downhill fast!

ohh and edit on my end, its not access logs that i was looking at to see who was on my network, its a DHCP client table, shows computer names and IP's, and no others were connected during a slow connection time.

---

### Post by computer13137 on 2009-07-05
As a disclaimer: I do not have DSL... but I have helped others to configure it.  lol.

First of all, DSL is significantly less impacted by "local torrenting" as suggested above.  Cable is more impacted by this because it's more of a shared infrastructure.  ADSL is a dedicated link back to the DSLAM at your telco, so there's a much larger backbone.  Torrenting on your "street" shouldn't have much of an effect on your connection speed.

Also, since the speed issue is showing up on your modem status page, it's not Ubuntu's fault.  The problem is one of a few things.

1) Your modem.
2) Your DSL line.
3) Your ISP's side.

Do you know how far you are from the ISP's DSLAM?  You may have a degraded signal quality.  Perhaps something they recently did has made it worse, and it's starting to affect your DSL signal quality?

If your speed tests on like, speedtest.net were slowing down, but your DSL modem still said it was connected at full speed, I'd be willing to say Ubuntu could be the problem.  However, since the issue exists on your DSL status page, Ubuntu has nothing to do with it. 

That doesn't mean others\myself aren't willing to help you out here, but I'm just clearing that up.  The best thing you can do is to **call your ISP** and ask them about it.

Also, as a rebuttal of another user above... other people leeching your wireless would use bandwidth.  This would slow down your speed tests.  However, the DSL modem status page is an indication of "signal quality" more than throughput.  If they were using the bandwidth, it'd still be there.  The DSL modem would still be connected at full speed - just that some of that speed would be in use, so speed tests and stuff would slow down.  Reading the original post, I do not believe this is the case in this situation.

I'm going to subscribe to this thread in case there's anything else I can do to help.

Cheers,
Kirk

---

### Post by tonycollinet on 2009-07-05
I would say a good first step would be to try a different modem/router. Can you borrow one from a friend?

Secondly - try reading the advice here - a lot of it is UK specific (anything relating to BT - British Telecom), and won't help you, but some of the other stuff (especially trying your master phone socket (the one closest to where the wire comes into the house) and disconnecting other devices, checking microfilters, and phone wiring - all worth trying)

[http://community.plus.net/blog/2007/07/02/broadband-speed-faults-how-to-diagnose/](http://community.plus.net/blog/2007/07/02/broadband-speed-faults-how-to-diagnose/)

---

### Post by Brandon Williams on 2009-07-05
Another thing to check is the channel being used. If there are other wireless access points in the area using the same (or an overlapping) channel, you might be experiencing increased loss when use of the other WAPs increases, and it could be the case that your router has trouble recovering from that when the problematic use goes down.

To check channel usage in your area, do this:
```
$ sudo iwlist scanning | grep -e ESSID -e Channel
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sms       Interface doesn't support scanning.

                    ESSID:"jitendernet"
                    Frequency:2.412 GHz (Channel 1)
                    ESSID:"08FX11005413"
                    Frequency:2.437 GHz (Channel 6)
                    ESSID:"Frank"
                    Frequency:2.462 GHz (Channel 11)
                    ESSID:"REKHA"
                    Frequency:2.462 GHz (Channel 11)
                    ESSID:"REKHA1"
                    Frequency:2.462 GHz (Channel 11)
```
In my area, there are 5 WAPs, 3 on channel 11, 1 on channel 6, and one on channel 1. These are the most commonly used channels, since 1, 6, and 11 have no mutual overlap. The three WAPs on channel 11 will be having trouble, because they will all conflict with each other. The two on channels 6 and 1 are probably fine (provided there are no other types of wireless devices broadcasting in the same spectrum). When I got my WAP, I switched it over to channel 1 specifically because of the channels being used by the other WAPs in the area.

Check [this wikipedia page](http://en.wikipedia.org/wiki/IEEE_802.11#Channels_and_international_compatibility) for more information about channel planning.

---

### Post by Spike1158 on 2009-07-05
@ computer13137 - I agree 100% for a fact this is not an ubuntu problem..just posted it on these forums because I believe people who use these forums dont mind helping out on these problems one bit, and i try to give back as much as I can in the process.
Ok, for the distance between me and my ISP's DSLAM, i could walk there in 10 minutes. And thank you for the info about how ADSL is a dedicated link, i did not know that, learn something new every day.

 > Perhaps something they recently did has made it worse, and it's starting to affect your DSL signal quality?They were digging up my street some time ago for "verizon fios" so this is a definite possibility.
When my modem says i have a 3300Kbit connection, speedtest.net says the same thing, around a 2.90Kbit/s down speed...when my modem says i have a 1056Kbit connection...Speedtest.net results drop to a similar speed, was 0.96Kbit/s result i believe. So results are definitely similar between modem/speedtest.net...and again this is on both computers and ANY OS. I'll post some screenies today of results between the 2.

Ok now @tonycollinet...im gonna try unbricking my new router that i killed today, and i will give it a shot if i can get it working, As for borrowing a different modem, no one has a similar modem as me that I know, but i can definitly give them a shot.
Changing phone line jacks is a good idea and I am gonna try that asap, and also a different phone cable.
And im multitasking by reading the guide and posting here right now lol..

In the long run I fear 
> The best thing you can do is to **call your ISP** and ask them about it.but I will hold out on that for now, and ty all for input again :)

---

### Post by Spike1158 on 2009-07-05
```
adam@adam-desktop:~$ sudo iwlist scanning | grep -e ESSID -e Channel
[sudo] password for adam: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

                    ESSID:"linksys"
                    Frequency:2.412 GHz (Channel 1)
adam@adam-desktop:~$ 
```

I've never had any other wireless network show up when scanning for the past year living here...but maybe someone has SSID broadcast disabled and i cant see em. I switched channels about a 2 weeks ago just to mark one more possible cause off the list, and nothing :(

---

### Post by Brandon Williams on 2009-07-05
Even with SSID disabled, you would still see the other WAP. It would just show a MAC address instead of an SSID. If you consistently get these results, you can be confident that there is no other WAP screwing up the channel for you.

---

### Post by Spike1158 on 2009-07-05
Ok, finally proof I'm not paranoid about this lol...
First, a normal connection speed. [http://i193.photobucket.com/albums/z189/Spike1158/Screenshot.jpg](http://i193.photobucket.com/albums/z189/Spike1158/Screenshot.jpg)
And the normal test speed at a very well known test site. [http://i193.photobucket.com/albums/z189/Spike1158/Screenshot-1.jpg](http://i193.photobucket.com/albums/z189/Spike1158/Screenshot-1.jpg)- both taken around 9am this morning, NO one else on the internet but me.

Now I've been playing F.E.A.R most of the day, getting the crap scared out of me, but no heavy internet use none the less. 
And now current results- [http://i193.photobucket.com/albums/z189/Spike1158/decrease.jpg](http://i193.photobucket.com/albums/z189/Spike1158/decrease.jpg)
and speedtest.net results- [http://i193.photobucket.com/albums/z189/Spike1158/test.jpg](http://i193.photobucket.com/albums/z189/Spike1158/test.jpg)

It has done pretty good today, considering it took all this time to happen. This is the 1st sign of this problem, from here, it usually drops in the 1000Kbit's and sometimes lower on speed.

All I'm looking for is someone to say something like "YAA, that happened to me, ISP issued a new router to me" or a certain modem/router setting is causing this. so again, ty to all for any input :)

---

### Post by computer13137 on 2009-07-05
I don't want you to feel like I'm insulting your intelligence, or patronising you, Spike1158... so please don't take it personally that I'm going to explain this so a third grader can understand it.

That is a DSL modem.  It measures the connection rate between your house and the ISP.  Either the link between your house and the ISP is the problem, or the modem is bad.  It has nothing to do with your WiFi, or neighbors broadcasting on the same channel, or the router, or your computer.  lol.

There's no magic command that's going to fix this.  If you're afraid to call your ISP for some reason, ask someone else in the area who has the service if they are experiencing the problem too.  Check their DSL status page and see if their speed is down too.  If it's not, then it's probably not the phone lines, it's probably your DSL modem.  If their signal is low too, they probably did bust a line installing FiOS.  That being said - if the lines are damaged, it's only going to get worse as the seasons change, and water gets into the system.  Eventually you're not going to have any Internet all.

Your ISP is there to provide you with good service.  Find out if it's their fault - and if it is - make sure they fix it.  You're paying for the service, so you're entitled to something.

Also, as a side note, I am curious... is there any packet loss?  Try sending like 50 packets to Google (might take some time) and paste the final loss report at the end of the ping, which looks like this.  If you're experiencing a lot of packet loss, that continues to point toward bad equipment or wiring.

```
ping -c 50 google.com
```

My output:
```
--- google.com ping statistics ---
50 packets transmitted, 49 received, 2% packet loss, time 49668ms
rtt min/avg/max/mdev = 49.576/60.525/191.979/20.175 ms
voyager@Voyager:~$ 
```

A little packet loss is probably normal, but anything over 5-10% would set off an alarm in my mind that something else might be wrong.

Good luck with this, hope you get your Internet back up to speed. :)

Cheers,
Kirk

---

### Post by Spike1158 on 2009-07-06
hehe, no I'm not offended, it takes a lot to do that. And no, I never suspected it to be a WiFi problem, both computers get the same results, so that was eliminated right away. But I've never seen a connection deteriorate like this is, so at 1st, all possibilities were open. 

```
--- google.com ping statistics ---
50 packets transmitted, 50 received, 0% packet loss, time 49071ms
rtt min/avg/max/mdev = 68.835/69.940/76.968/1.139 ms
adam@adam-desktop:~$ 
```Definitely not the problem, and that's the results from my connection being half of what its supposed to be.

It's not that I'm afraid to call them, I just know I'm gonna end up on the phone for hours with them doing the whole, is this cable pluged into here, and this to there...ok reset you're modem for 30 seconds. Ugh, lets just say my last problem that I had with my modem took like 4 different tiers of "specialist" to solve my problem, and they ALL started out with the wire here, wire there, reset for 30 seconds deal. Ended up having to change my VC bridge settings to Routed Bridge mode for my modem to work with a seperate router rather than act as a router, its labeled as a modem/router...lol, ya right.

Maybe I have some form of a bandwidth limit that I have no clue about. Anywho, thank you all for input, and I guess this weeked I'll buck up and call Verizon. And if i decide to take a baseball bat to anything, I'll post some office space style pictures :)

---

### Post by computer13137 on 2009-07-06
> **jocoolguy said:**
> to speed up internet, delete all temp files, clear cookies, after doing this try internet and test your speed 
[ here ]("http://www.ip-details.com/internet-speed-test/")

Once again... DSL modem link speed.  This will not do anything to fix his problem.

-Kirk

---

### Post by LewRockwell on 2009-07-16
Linksys BEFW11S4 V4 Firmware 1.52.03 Update Error Solution Provided!

I must have missed the post about making sure the firmware was most current so I'll help out by providing several links.

Firmware Download Page:
[http://www.linksysbycisco.com/US/en/support/BEFW11S4/download](http://www.linksysbycisco.com/US/en/support/BEFW11S4/download)

Forum where others are relating the solution to a problem flashing:
[http://forums.linksys.com/linksys/board/message?board.id=Wireless_Routers&thread.id=125251](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Routers&thread.id=125251)

And here is the solution in case the above forum link goes bad:> The BEFW11S4 apparently has trouble with long filenames for the .bin files.  So if you get the "Upgrade action is not finish!! Upgrade failed!" error when you try to update the firmware to the latest version, just rename "BEFW11S4-v4_v1.52.03_fw,0.bin" (or whatever it is) to code.bin and then try again using the code.bin file.

This solution worked for me as of 07/16/09 and I wanted to pay-it-forward by making sure it was posted on our wonderful Ubuntu Forum!

.

---

