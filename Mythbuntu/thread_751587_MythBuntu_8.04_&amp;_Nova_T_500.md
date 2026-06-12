---
title: "MythBuntu 8.04 &amp; Nova T 500"
date: 2008-04-10
forum: Mythbuntu
---

### Post by RobJohnston on 2008-04-10
My myth box has gone bonkers so I want to re-install this weekend, I'm planing to go up to 8.04 beta.

Reading around there is conflicting reports of it working better ... working worse ... EIT still a problem ... compile the kernel ... etc. Can anyone tell me how they get on with the nova-t-500 under 8.04 beta?

Take care, Rob.

---

### Post by superm1 on 2008-04-10
Was that the USB bug you are referring to?  If so, that's been fixed.

---

### Post by RobJohnston on 2008-04-10
I'm referring to the disconnects and the partial locks. It's quite well documented but I can't find the post or quote that gives me the green light with 8.04

---

### Post by superm1 on 2008-04-10
Well if the nova t-500 is the usb device, I recall a bug on a usb adapter w/ lots of disconnects being fixed.

---

### Post by Nikas on 2008-04-11
> **superm1 said:**
> Well if the nova t-500 is the usb device, I recall a bug on a usb adapter w/ lots of disconnects being fixed.

Yes. Thats the one.
It's a PCI-card with two built in turners and usb-controllers that connects the tuners to the PC.

---

### Post by superm1 on 2008-04-11
> **Nikas said:**
> Yes. Thats the one.
It's a PCI-card with two built in turners and usb-controllers that connects the tuners to the PC.
OK then I wasn't getting things mixed up.

Should be fixed w/ the latest kernels available in apt.  So if you install the 8.04 beta, just do all the apt updates and you will be in good shape.

---

### Post by RobJohnston on 2008-04-11
Splendid! Thanks for your advice.

Rob.

---

### Post by Freddie on 2008-04-11
Sadly I have had no such luck with the latest kernels with my Nova-T 500. A variable amount of time after booting up the card would disconnected requiring a reboot to fix.

Regards, Freddie.

---

### Post by superm1 on 2008-04-12
Freddie, that's very depressing to hear, particularly this late in the game.  I had last heard these things were functional again.  Do you have a patch or some information that we can track down to see to a fix?

---

### Post by Lem on 2008-04-14
I took the NovaT 500 out of my 8.04 set-up. I've just accepted that it's not going to work. Shame as the picture quality is excellent and it does the 'multiple channels on one multiplex' trick which my standard NovaT doesn't seem to do.
I think the problem is down to signal quality. If you've got a good signal then this seems to work, but if you're in a weak signal area then it will disconnect quite frequently.

---

### Post by RobJohnston on 2008-04-15
It's frustrating as some people seem to have no problems with the Nova-T 500.

Previously I had it quite stable with the EIT turned off but I had problems with the XMLTV program guide. I'll try it again see how that goes under 8.04.

Rob.

---

### Post by TheConsultant on 2008-04-15
Hi @all.
I have some trouble with 8.04 mythbuntu.
[LIST]
[*]At first the mythbrowser is not working well with the IR remote (no reaction).
[*]With the IR remote: After you have called a site inside the newsreader, he is jumping back to the informations page as you have pushed the esc button for two times. With keyboard it is working well.
[*]VNC is not setting up by the MCC.
[*]I'm missing the aspect ratio check box in the play back settings, because onto my 16:9 TV must switching to a 4:3 aspect ratio play back for a correct play back 16:9 format.
[*]It is not possible to shutdown with the IR remote Power off button.
[*]Mythwelcome is not working well, because no F11 or F12 buttons on the keyboard are acceptet and mythwelcome is not shutdown the PC with correct shutdown settings.
[*]German OFDB.PY is not working
[*] Mythmovies only available for US country cinemas (oh yes - I'm german)
[*] a tail -f /var/log/syslog shows a "dib0700: Unknown remote controller key :  3 20" each second
[*] A 'dpkg-reconfigure xserver-xorg' gives me not the choice to setup the resolution, only the keyboard and language settings. My TV is not correctly recognized. By the way, the graphical resolution settings tool is only knowing PC monitors and no TVs - why?
[*] The mcc is not correctly setting up the PC for autostart configuration of mythtv
[/LIST]
Tipps and Tricks are welcome.

Best regards

Martin

---

### Post by Al_Vampyre on 2008-04-19
Hi Rob,

I managed to solve the disconnects issue on my 7.10 setup with a script called 'MythWatch' which I found by googling. My apologies to the person that wrote it but I've forgotten their name.

Basically it watches the backend for a disconnect then restarts the card when it spots one. My 7.10 is working flawlessly now!

---

### Post by RobJohnston on 2008-04-21
I'm hoping this won't jinx my setup.....

My nova-t 500 seems to be working fine with 8.04, I've had one recording go wrong (of over 50 OK) and I'm not sure I can blame that on the disconnect issue.
I used mythwatch on 7.10 before and according to the log for that I was getting 2-3 disconnects a day, so it's a great step up from that.

The one improvement I've made to the system is adding an external signal booster.

I'm very pleased with how it's working, hopefully it'll be this way for some time to come.

Thanks, Rob.

---

### Post by zzztownsend on 2008-04-22
Hi folks - have tried googling but no luck - anyone know where I could get the mythwatch script from - I'm going to give it a whirl. I get the disconnects problem, but only on one of the tuners so I have been limping for a while but tolerating it until I get time to tinker

cheers

matt

---

### Post by RobJohnston on 2008-04-22
It's here:
[http://ubuntuforums.org/showthread.php?t=618546&highlight=mythwatch&page=2](http://ubuntuforums.org/showthread.php?t=618546&highlight=mythwatch&page=2)

It restarts the backend when it discovers a disconnect, this can ruin a recording or drop any frontends connected.

I did use it and it helped alot but 8.04 feels much, much better.

Good luck, Rob.

---

### Post by RobJohnston on 2008-04-23
Just had my first major disconnect, missed about 5 shows yesterday on one tuner.

Looks like I'll put mythwatch on to keep a log of how often it happens.

Not perfect but still better than before.

Regards, Rob.

---

### Post by Hugolp on 2008-04-28
Same here. I would like a lot Hardy if the Nova-t-500 would not disconect randomly. I am missing a lot of my recordings becuase of this and is very anoying, specially because it was working perfectly in Gutsy. Anyone has discover a solution?

Hugo

---

### Post by GordonEndersby on 2008-04-28
Since installing 8.04 on my box with 2 Nova T 500's Ive had only 2 backend crashes and I cant say its anything to do with the 500's.
Ive got Monit installed to pick up any backend failure.
I havnt had any failed recordings since last week when I installed 8.04
Install monit 4.1 as it has email support and use the monitrc supplied.
[http://mythtv.org/wiki/index.php/Status_Monitoring_How_To](http://mythtv.org/wiki/index.php/Status_Monitoring_How_To)

Gordon

---

### Post by Hugolp on 2008-04-28
In my case the nova-t-500 hasnt crash my backend (not even once). The problem is that with hardy, most of the time it wont lock on the channel. The installation is the same that didnt have this problem (not even once) in gutsy. My third turner gets the signal from the same cable and is working fine. Sometimes the nova-t-500 will lock the channel and it will work, but most of the time it wont, so when the backend tries to record something, I will find most of the time, recording failed, and so I know most of my recordings wont get recorded.

I have tried adding the line:

options dvb-usb-dib0700 force_lna_activation=1 

to /etc/modprobe.d/options but still no solution.

And if I do dmesg in the backend I get lots of this:

[168629.427367] mt2060 I2C read failed
[168629.435369] mt2060 I2C read failed


Hugo

---

### Post by GordonEndersby on 2008-04-28
I have heard that these cards need a strong signal.
When I split my aerial I used an amplifier as I wasnt sure what would havppen to the signal.

Im getting 53% - 63% signal strength and I have an old digital aerial from the early days of digital TV.

What type of aerial and signal strength have you got.

Gordon

---

### Post by Hugolp on 2008-04-28
> **GordonEndersby said:**
> I have heard that these cards need a strong signal.
When I split my aerial I used an amplifier as I wasnt sure what would havppen to the signal.

Im getting 53% signal strength and I have an old digital aerial from the early days of digital TV.

What type of aerial and signal strength have you got.

Gordon

The same one that was working fine with this card and Edgy, and Feisty, and Gutsy... I did have some problem at the begining of Edgy but a v4l patch solved it. While upgrading to Hardy I havent even moved the computer or the antena cable, and it has stoped working. Plus getting those dmesg messages points to something not working and not a signal level problem. I get more than 40% signal in the worst channels. Usuall I get from 50 to 70% in most channels.

Also, do you know that signal strenght is not the only variable to get a good tuning?. You know that adding an amplifier prior to the split could make things worst?

Hugo

---

### Post by GordonEndersby on 2008-04-28
The amplifier I have allows you to adjust the signal strength.
It has two outputs that I patch to my dvb card.
If I turn it up too much I get too much noise and the card doesnt like it and  cant get a lock. but when I get it just right the signal is stronger and theres no detectable noise by the card.
I did have one duff coaxial lead I had to throw out.
I had this on 7.1 and now 8.04. without any problems.

The only difference I can think of is that im using the release candidate still. Im going to be re-installing with the full release shortly due to some other problems Im having that the weekly fixes arnt sorting out, DVD playback and archiving, Maybe mine will break with that?

---

### Post by Hugolp on 2008-04-28
Yes, but amplifiers are real-world devices so they introduce distorsion on the signal, so sometimes if the signal is enough is better to not put any amplifier to avoid the distorsion they introduce. In case you need to put an amplifier because the signal is not strong enough is usually better to put it at the begining of the circuit and not at the end. This is because of this:

Amplifier at the end:

antena-> low level signal-> cable wich introduces noise and afects the signal more because the signal has low level-> amplifier that has to amplify a lot because the signal is low level, so it amplifies a lot the noise of the cable too -> distorsion introduced by the amplifier -> device

or the amplifier at the begining:

antena -> low level signal -> amplifier that amplifies the signal -> distorsion introduced by the amplifier -> cable wich introduces noise (just as before) but because the signal is a lot more strong, relatively the noise is a lot more insignificant -> device

The point is that if you amplify at the end, you amplify also all the noise that it has gotten through the circuit, and if you amplify at the begining you dont, plus the signal is a lot more strong and gets affected a lot less by the noise. In both cases you get the distorsion introduced by the amplifier.

Just for you to know. Probably I am being too ******* and at the end the solution that works is the good solution, but I studied telecomunications engineering... So if you can try to put the amplifier at the begining of the whole thing, and allways try if the system works without amplifier cause that way youll avoid the distorsion it introduces. But if your system is working fine this way dont touch. DVB-T is digital, meaning that once you get the signal right, any improvement on the comunication levels doesnt do anything because you allredy got the right digital signal.

More on topic, hope your system works well when you update to the definitve version. I have installed the definitive version directly, and havent found a solution yet.

Hugo

---

### Post by Elis on 2008-04-28
Hi, I have the Nova-T-500 too and with Mythbuntu 7.10 it works ok if I change the two settings "ATSC Signal Threshold (%)" to the lowest and "Time limit for ATSC signal lock (msec)" to the highest. Otherwise with the default settings of whose two it won't work, or work very bad.

I can't find those settings in the 8.04 version. Are they still there or have they been removed? My 8.04 installation is almost unusable right now with all the default settings.

---

### Post by GordonEndersby on 2008-04-29
This morning I did a fresh install of 8.04 and it works as well as the release candidate. Hasnt solved my problems with DVD playback and archive not working but my 2 Nova T 500's are both working perfectly.
If theres anything on my system that you want to see in the way of logs, configuration or other hardware that would help you, let me know.
Probably best by private message as its taken me a while to trawl through to find this message.

Threshold and time limit are on the backend configuration where you add the card.

Gordon

---

### Post by Hugolp on 2008-04-29
Hi

About your dvd's problems, I believe that Hardy comes with Mythtv 0.21 wich doesnt use mytharchive anymore, becuase the dvd are handeled by mythvideo directly. So if you install mythvideo you should be able to see dvd, just like you did with mytharchive before.

About the system, I would apreciate if you could send me a private message after a week. At the begining I had no trouble, but after a couple of days started hitting me. So if you could tell me something in a week a would apreciate it.

Thanks

Hugo

---

### Post by GordonEndersby on 2008-04-29
Hugo,

It just occurred to me this afternoon I dont know why I didnt remember this, I put it down to old age.

When I was experimenting with Mythdora before looking at Muthbuntu I had some problems with the Nova T 500 because I had placed my DVB card too close to the passively cooled graphic card. The heat sink was only a few mm from the dvb card. It worded fine for a while then got too hot too touch and started to cause problems.
Normally the card wouldnt get to hot on its own.
It couldnt be something similar could it?
Another heat source overheating the DVB card?

Ive sorted the DVD problem now.
I had to install the additional codecs via the control panel to allow reading of encrypted DVD's.


Gordon

---

### Post by Hugolp on 2008-04-30
> **GordonEndersby said:**
> Hugo,

It just occurred to me this afternoon I dont know why I didnt remember this, I put it down to old age.



Good you sorted your dvd problems. About the nova-t-500 not working, I am almost sure that its because a problem of the kernel handeling usb. There is a patch that solves this bug, but it seems it wasnt aplied. Its a regresion. And it seems due to some users demands it got solved in the later release candidates, but dont know why the final release didnt got the patch. I am hoping that in the next kernel actualization it will get solved but who knows. You can check in Launchpad the discussions and coments about this issue.

Also, to be sure, when this happens to you, can you do a "dmesg" in your backend and print here the last lines?

Hugo

---

### Post by GordonEndersby on 2008-05-01
Ill keep a close eye on it and wait and see if I get any problems.
Ill post the logs if it breaks.

I had a bit of breakup on my second card yesterday.
It turned out to be a loose aerial connection as I have been pushing and pulling the case out of under the TV.
The cables I have between the amplifier/splitter arnt the best quality.

Gordon

---

### Post by Hugolp on 2008-05-01
To anyone following this thread and having the same problem with the nova-t-500, you can report it in this bug report of lauchnpad so it will get more attention and hopefully will get solved sooner.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204857](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204857)

Hugo

---

### Post by superm1 on 2008-05-01
> **Hugolp said:**
> Good you sorted your dvd problems. About the nova-t-500 not working, I am almost sure that its because a problem of the kernel handeling usb. There is a patch that solves this bug, but it seems it wasnt aplied. Its a regresion. And it seems due to some users demands it got solved in the later release candidates, but dont know why the final release didnt got the patch. I am hoping that in the next kernel actualization it will get solved but who knows. You can check in Launchpad the discussions and coments about this issue.

Also, to be sure, when this happens to you, can you do a "dmesg" in your backend and print here the last lines?

Hugo
I'm sure the patch did get applied:
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=commitdiff;h=a76cacbd9926c804f670c6717209876172dd7bf0](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=commitdiff;h=a76cacbd9926c804f670c6717209876172dd7bf0)

---

### Post by Hugolp on 2008-05-05
Solution founded:

[http://ubuntuforums.org/showthread.php?p=4887362#post4887362](http://ubuntuforums.org/showthread.php?p=4887362#post4887362)

Hugo

---

### Post by tidderd on 2008-05-06
Hi,

I also have the Nova T500

I was running Mythbuntu 7.10 and got the machine up and running great before I installed the DVB card.

When I installed I had read a lot of the posts on the Nova T500

I followed these two How Tos

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)

I still got the disconnects, which I traced back to the remote.

It errors if your dont have the remote sensor connected, not a problem for me as I am using a MCE USB remote, I therefore 'disabled' the option

The important part in the two How Tos above is to get the 'options' correct.

For me they were;

options dvb-usb-dib0700 force_lna_activation=1
 - boosts the signal

options usbcore autosuspend=-1
 - stops it from going to sleep thereby giving the disconnects.

options dvb_usb disable_rc_polling=1
 - disable the on-board remote control. This is the bit that was   giving me errors in demsg relating to MT2060 and worryingly 'over current warnings.



I have since done the online upgrade to 8.04 - about 5 hours worth :(

All working fine in the upgraded 8.04, same as it was in 7.10.

Have had it running almost none stop since @25th April doing various recordings, dont watch much LiveTV but it has done multiple records at the same time.

All Good.

Liking Mythbuntu 8.04

The Greyheim theme looks well kwel when used with a black LCD screen

---

### Post by sdjkfhk123j4h2jk on 2008-05-06
Thanks tidders, I just applied all your changes, let's see how it goes...

That means that right now I don't have a remote! But I prefer that than losing recordings.. I'll use an external keyboard or vnc.

Regarding the MCE Usb, did you get it from Ebay? Maybe I'll get one of them. The problem is that a few months ago I got one from ebay that actually acts as an HID mouse and keyboard. And the guys who did it didn't even include the direction arrows (it has something like that but it actually moves the mouse). So now I don't know which one to get, I want a real MCE remote that works with lirc.

---

### Post by Nikas on 2008-05-06
Have you done this? 
[http://ubuntuforums.org/showthread.php?p=4887362#post4887362](http://ubuntuforums.org/showthread.php?p=4887362#post4887362)

I have never used the built in receiver. I have built my own serial receiver but i use the remote that came with the cards. I'm not using EIT and i have never had any problems. :)

---

### Post by sdjkfhk123j4h2jk on 2008-05-11
I tried every single possible solution (disabling remote, modules options, installing mythwatch, etc) without success. But finally I found what really makes the difference:

- Go to mythtv-setup, to the tuner cards, and disable the eit scanning (it will still get the eit programming by passive scanning when you are watching or recording), and also choose the option to not to lock up the card unless it's in use.

I haven't got any problems since.

---

### Post by drifting on 2008-05-13
Ok, well being rather dumb, and not able to find any information anywhere else, is the Nova-T 500 supported directly in Mythbuntu 8 Or do you still have to go through the driver rigmarole ?

Paul.

---

### Post by GordonEndersby on 2008-05-13
When I re-installed 8.04 with two nova t 5oo's  after trashing my old 7.10 they were supported without having to install the latest v4l libraries.

Gordon

---

### Post by oct on 2008-05-18
I'm having issues with Nova-T 500 and Mythbuntu 8.04, too. Mine are these:

- From time to time, when changing channel, I get a "You have gotten a channel lock..." message. After 1 or 2 seconds the channel change correctly and the messge disappears. I have to do nothing (accept, hit "Esc", reboot). This happens about 1 of every 10 changes. With 7.10, when the message appeared, I had no video and had to jump to another channel, or stop watching TV and starting again. But this happened only 10 or 12 times within 6 months of daily use.

- The other issue and the most annoying one. is that the playback becomes very choppy whan using the remote control. I use the Hauppuauge remote with the IR receiver connected to the Nova-T. I have verified that this also happens when watching a recorded show, not only with live TV. I can't even change volume without problems. When I stop playing with the remote control, the playback is good. With 7.10 all was smooth.

Can anybody help me?

Thanks 

Oct

---

### Post by xykevinr on 2008-06-16
I've finally got my Nova-T 500 working reliably (and that means working 24/7 for a week without a failed recording).

My current settings are

1. EIT scanning disabled
2. usbcore autosuspend = -1 (thanks tidderd !)
3. disable remote polling
4. 200ms tuning delay.

I KNOW that if i change either 1 or 2 I will get failed recodings within 48 hours.

I dont know if changing 3 or 4 make any difference to me. 

Hope this helps someone !!

Kev

---

