---
title: "Don't find all wireless connections"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by Zalastax on 2010-04-21
Hi!
I got this odd situation :
I installed ubuntu 9.10 yesterday and it runs fine except that I can't find all internet connections.
Yesterday I found up to 3 wireless networks but never my own and all with password.
I tried to search the internet to get help solving the problem but nothing worked.
I did a lot of stuff and the only thing that happened was that I couldn't even see the wireless network tab in internet connections.
So today I reinstalled ubuntu 9.10 and I can find 1 wireless network(the same one that appeared first yesterday)

The network I want to find is called krafft (by windows 7) and the SSID is krafft, the type of safety is WPA2-Personal and encryption type is AES. I tried to acces it via the option access hidden network but it couldn't find anything.

I get wireless connections via D-Link DWA 140 with rt2870 drivers (ralink).
My system is 64 bit.

---

### Post by mikewhatever on 2010-04-21
Since you tried accessing it through the 'hidden network' option, is it safe to assume your network hidden (not broadcasting its SSID)? If that's the case, you'll have to enable SSID broadcasting to 'see' the network.

---

### Post by Zalastax on 2010-04-21
I love this forum! So quick replies!
I think that the server is broadcasting SSID because when I check the network properties in windows it tells me that the SSID is krafft.
Is it possible to connect to a network that don't show up in ubuntu but does in windows?
I just don't get why I don't see all networks that are available in windows over in ubuntu.
Are there any numbers or settings I could look up or change in windows to make it work in both Operating Systems?

---

### Post by bkratz on 2010-04-21
> **Zalastax said:**
> I love this forum! So quick replies!
I think that the server is broadcasting SSID because when I check the network properties in windows it tells me that the SSID is krafft.
Is it possible to connect to a network that don't show up in ubuntu but does in windows?
I just don't get why I don't see all networks that are available in windows over in ubuntu.
Are there any numbers or settings I could look up or change in windows to make it work in both Operating Systems?




You can see all available wireless A/P's  and the basic encryption types by executing the following in the terminal (Applications>>Accessories>>Terminal)

```
sudo iwlist scan
```

Do you see your's there?  Since this is a "sudo" command it will require your password which will not be echoed to you. Just hit enter when done.

---

### Post by mikewhatever on 2010-04-21
If the SSID is visible in Windows, then it's not hidden, and you should also see it in Ubuntu. Sometimes, changing the channel helps, as the Linux driver may not work with some of the channels. There should be an easy web based GUI to manage your router, wireless settings including.

---

### Post by Zalastax on 2010-04-21
I will try what you told me tomorrow and come back and tell you the results.
Thank you for everything!

---

### Post by Zalastax on 2010-04-22
Now I have tried both your advices.
When I tried the sudo thing it said that it didn't support the options in all four tabs that appeared.

I also tried to change channel to the lowest and the highest and the one in the middle but no changes at all.

I think the problem is somewhere else.

Today also a new network showed up : Glocalnet Wireless (another locked one)
so there is nothing wrong with the internet receiver.

Are there any possibility to create a new network that is optimized for linux and have the other network left?

---

### Post by P4man on 2010-04-22
Can you disable the WPA temporarily on the access point to see if that solves it?

---

### Post by Zalastax on 2010-04-22
Thanks!
After I disabled the WPA I could find the network.
But I couldn't connect to it :(
Here are the results after I did some iwlist commands :
Available channels : 
```
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)
```iwlist scanning ( not scan,it didn't work) :
```
sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:F3:79:C2
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=39 dBm  
                    Encryption key:off
                    ESSID:"krafft"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000014c08180
                    Extra: Last beacon: 1400ms ago
                    IE: Unknown: 00066B7261666674
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603001800000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403000000000000000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD0E0050F204104A0001101044000102

```

---

### Post by P4man on 2010-04-22
okaaay..
before delving any deeper, did you install all updates on ubuntu? Which kernel are you running (if you dont know, open a terminal and type

```
uname -a
```

)

And did you actually download and/or compile these drivers, or using what comes with ubuntu?

---

### Post by Zalastax on 2010-04-23
I haven't installed anything on ubuntu since I installed it from the latest ISO on ubuntu.com

The kernel is : 2.6.31-14-generic #48-Ubuntu SMP  x86_64 GNU/Linux

and I haven't installed any drivers or such because I saw on some excel file that my USB-Internet receiver was supported right out the box.

My only problem now is to connect to the network (I still can't find it if it has WPA but I can reach it if I turn that of).

---

### Post by P4man on 2010-04-23
First thing to do is run update manager and download/install all updates. You might be running into a bug which has been fixed meanwhile

---

### Post by Zalastax on 2010-04-23
The thing is that I can't connect to internet and my computer is stationary.
If I want internet to it I would need to take it down from upstairs and connect it wired.
And I also thinks that the hardware have been supported for quite a long time, am I right?

---

### Post by P4man on 2010-04-23
> **Zalastax said:**
> The thing is that I can't connect to internet and my computer is stationary.
If I want internet to it I would need to take it down from upstairs and connect it wired.
And I also thinks that the hardware have been supported for quite a long time, am I right?

Ah, damn, nice catch 22 there.
From what I remember googling, it was supported under (and I think only since) 9.10, depending on the version. 

I just saw these:
[http://ubuntuforums.org/showthread.php?t=1441436](http://ubuntuforums.org/showthread.php?t=1441436)

and

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1333255](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1333255)

Its definitely not a card that always works out of the box, and apparently there are different versions of it. Reading those threads should help you though I think. But following the instructions might get tricky when you're not online. Perhaps try the blacklisting trick first (post 3 in the second link).

---

### Post by Zalastax on 2010-04-24
Thanks!
Now everything works.
I used the blacklist and then I could connect to internet after I disabled WPA-Personal in the network.
And after I updated Linux I took WPA-Personal back and It could still find the network.
So internet works fine now(I'm writing this from Ubuntu)

I just wonder why my computers fan is on all the time, It's just like when I start-up windows but all the time, in windows it is only on before log-in screen but not in Ubuntu.
Any Ideas? I will look around to see if anyone knows a solution.

---

### Post by P4man on 2010-04-24
Id suggest opening a new thread for that (be sure to include information about the computer brand/type) and mark this one as [solved]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6")

---

