---
title: "Intermitent wifi connection due to jammed frequencies?"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by Margaret Dumont on 2013-01-27
Dear all,

I have problems with my wifi and I've checked other threads but they do not seem the same kind of problem.

-------
I'm not 100% sure this particular part of the story is related to the problem but I prefer to explain it just in case:

Some months ago, I had been using my internet connection for a long time with no problem, when suddenly my computer started to be able to connect to the wifi only intermitently. At booting the computer would normally connect, although not always, but if it was starting from hibernation the connection was lost and wasn't be able to connect again unless rebooted (I could always see the wifi but in those cases it kept asking for the password over and over). Sometimes I would even have to reboot more than once for it to work.

One day the issue stopped as it had started without me doing anything in particular and it's been several months that I haven't had that problem again. I simply assumed it was some Ubuntu bug that got fixed with one of the automatic updates, but now I think it might be related to the problem I have now.

--------

A couple of days ago I've started having problems again, but this time not even rebooting would get it to connect (I've been without internet connection in this computer for a while). Finally, I discovered by accident that if I brought this laptop near the router, it would connect with no problem, and once connected, I could bring it back to my desk and continue working without getting disconnected. But if rebooted in my desk, it wouldn't be able to connect, and I have to bring it back to the router every day before I start  working.

For the reason I've just explained, I'm pretty sure that my problem has nothing to do with configuration or security issues but rather signal reception. It seems that, for some reason, it needs a better communication with the router to connect to the wifi than it needs to keep the connection alive.

Just to clarify, I always see my wifi, when it say it cannot connect is because it just keeps asking for the password (which I just ignore because it's useless to provide it). And when I say that it can connect, it means that it does it automatically without asking me the password at any point.

----

I know there are a lot of wifis around cluttering the signal because from time to time the wifi starts getting horribly slow at peak times (while still having a good connection through the cable), and I have to try getting my router to send the signal through other frequencies by changing the channel to be able to regain a reasonable speed. And, in fact, I get about 50 other wifis in my place. Unfortunately, I'm under the impression that some of the other routers keep changing their frequencies to a random channel because I have to keep repeating this procedure from time to time.

1) So, does anyone have any idea why that may be happening and how to get around it? Even if I had to run some kind of script every day form my laptop to be able to connect to internet, it would still be much better than having to move the computer around.  :)

2) It does not solve my problem but, apart from that, I am seeking a program that can scan and display the frequencies that existing wifis are using so that I can avoid them. The problem is that the feature descriptions of candidate programs that I've found are a bit too technical and I don't know if they are suited to do that. Are [netsniff-ng]("http://netsniff-ng.org/") or [Kismet]("http://www.kismetwireless.net/") right for this task?

Or is there any easy way that I could check the quality of the signals I am receiving from my computer at different frequencies so that I know which is the appropriate channel, instead of going through trial and error? 

Thanks!

       Margaret

PD: I am using Ubuntu 12.04 LTS and I believe the wireless card in my latptop is an Intel Wireless WiFi Link 4965AGN.

---

### Post by ahallubuntu on 2013-01-27
802.11n uses two base frequencies: 2.4GHZ and 5GHZ.  Cheap routers use only the 2.4GHZ base frequency.  This frequency is used by many devices (other routers for example) and is prone to interference.

A dual band router can use both 2.4GHZ and 5GHZ ("simultaneous dual band" can do both at the same time).  You could consider trying one of those and try 5GHZ and see if that improves your resistance to interference.  I have heard reports of such recently from one person I know.  Not all wireless card can do both 2.4GHZ and 5GHZ, but your 4965AGN can.  But you need to have a router that can do both frequencies ("dual band") also.

---

### Post by steeldriver on 2013-01-27
2) if you are using a standard desktop version (with network-manager) then you can use the nm-tool command line program to display all the adjacent access points with their strengths and frequencies 

```
nm-tool
```or you can get a (imo) slightly neater version with the command

```
nmcli dev wifi list
```It should give you all the info you need to choose a good channel - it doesn't give a nice graph like some of the 3rd party tools (I've used inSSIDer on Windows but I don't know what to recommend in Linux)

[You could also use 'sudo iwlist scan[ning]' but that spits out a LOT of info which makes it harder to read]

---

### Post by Margaret Dumont on 2013-01-27
Ahallubuntu, thanks for the tip on the dual band technology, I had no clue. I've checked my router brand and model (Astoria Networks ARV4518PW-A-LF-LT... Is it [this one]("http://wiki.openwrt.org/toh/arcadyan/arv4518pw")?) and I think it does not have the dual band option.  :(  

I'm not totally sure it would be a good idea to change the one the ISP provides, taking into account that I would have no idea on how to configure it, but even so I cannot afford to buy a new one for the moment, so until then I will have to keep that option on hold.   :P

As I was taking a look at the router's configuration to see whether I could spot a dual band option, I've come across a list of the attempts to access my network. It has surprised me that there are a lot of something called "SYN flood"s attacks, up to 14 in some of the minutes (I was successfully connected at that time).

3) Do you think it is possible that I'm having some kind of attack that knocks out my router and that's why I'm having those problems? Or is that just an effect of having Transmission running? Any idea on how can I find out if they are legitimate attempts?

---

Thank you for the commands, Steeldriver, I'll try to determine the emptiest channel.  :)

Do you know if these commands create a log file somewhere that I can use to analyse the data so I can import it to a spreadsheet and easily draw my own graphs?

---

Best regards,

           Margaret

---

### Post by steeldriver on 2013-01-27
you can redirect the output to a file and import it into your spreadsheet program

```
nmcli dev wifi list > *myfile*
```

---

### Post by ahallubuntu on 2013-01-27
In my experience, the wireless router that an ISP provides is usually not of great quality.  When you can afford it, consider upgrading to a new one.  If this router is a "modem + router" that also connects to a phone line, you might need to keep it anyway but disable the wireless and connect a new router, perhaps a dual band router, someday!  Let's hope you could find a friend to help you set it up.

The attacks you mention are probably coming from the internet not from a WiFi.  If someone tries to connect to your WiFi, the only indication you would get is that someone tried to connect but their password was invalid.  You said originally that your wireless worked better when you got closer to the router, right?  If that is true, then it is probably interference as you said in the first place.

The idea from steeldriver is a good idea, though.  Wireless routers operating on 2.4GHZ use slightly different "channel" frequencies to avoid interference.  In the US there are 11 approved channels all close to but not exactly the same frequency.  In Europe I think there are 13 approved channels/frequencies.  In any case, the trick is to see if someone near you is broadcasting on the same exact channel as you.  If say they are broadcasting on channel 6 and your router also broadcasts on channel 6, you should change the channel to be closer to 1 or to 11 (or 13) to help avoid interference.

I don't have any experience with these monitoring tools in Linux so I can't give you any more tips.  You could search the web for more information about monitoring wireless channels.

---

### Post by Margaret Dumont on 2013-01-27
Thank you both for your help! 

In principle any computer with a mac address which is not listed is blocked from the wifi, so I suppose you're right about those attacks directly coming from the internet.

Indeed my idea was to keep trying to avoid crowded frequencies, as I have been doing until the moment, but now these tools will let me do it with much less effort. The redirection worked as a charm, so I am now looking the way to import the data file.  :)

However, I was hoping someone had an idea on how to help the laptop connection with the router to succeed even if takes a long time... I don't know, couldn't I tell the router to be more patient with my laptop somehow or to talk more slowly? If I got it to connect, even if that took 15 minutes, that would solve my problem already.  :)

---

### Post by Margaret Dumont on 2013-01-28
Hi all,

I have added the strengths of the different wifis at each channel and I've come up with the attached graph. Actually, taking into account that this graph is the result of adding up 50 different wifis I was expecting a much more spread occupation. With everyone concentrated in the same regions it doesn't look that hopeless to avoid the signal jams.  :)

My router was right now sending the signal through channel 6 (around 2437 MHz), which seems like it was the second worst option.    :(

I've heard somewhere that when you are using a certain channel you partially occupy the adjacent ones, so that it's not only about using an empty channel but also trying to avoid being near a crowded one. Do you know how wide is that range? Does it span just to the immediate nearest neighbours or further away?

If this is true, I'm thinking perhaps to change it to channel 9 (around 2452 MHz). What do you think?

Thanks,

         Margaret

---

### Post by Margaret Dumont on 2013-01-28
Hey! It worked! I'm so happy!   :)

Thanks to everyone!

---

### Post by steeldriver on 2013-01-28
well done!

---

