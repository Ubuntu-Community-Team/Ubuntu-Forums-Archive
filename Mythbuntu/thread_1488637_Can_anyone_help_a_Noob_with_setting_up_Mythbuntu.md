---
title: "Can anyone help a Noob with setting up Mythbuntu?"
date: 2010-05-20
forum: Mythbuntu
---

### Post by bance on 2010-05-20
Hi all,

I am very new to Linux, it's a very steep learning curve but enjoyable (frustrating) none the less.

I have made a fresh install of mythbuntu 10.4,
my hardware is :-
[LIST]
[*]intel celeron r 2.8 ghz
[*]1 gb ram
[*]75 gb hdd
[*]hauppage dvb-s/s2 4000
[/LIST]

I have searched the net for guides, and found "parker1" 's....  OK.
I've followed the guide, and so far I've been able to check that my TV card works under Linux.
I can scan for channels using dvbscan, I can tune to a channel using t/szap, I can watch TV using mplayer.
I have been able to create a channels.conf file.

OK onto myth set-up, Backend :-

General--- OK

Capture cards--- I set the dseq options for sat input-- ok
                 When I look for dseq options for dvb-t, I get the sat options (switch,rotor,LNB). I've tried using LNB option but it won't stay set!

Video source--- OK

Input connections--- This is where I come unstuck! When I try to scan for channels, the scan starts ok, but I get no joy. looking at Xterm it says some error about dseq tree, I guess that's to do with the problem stated above. Also in this section, the field for starting channel is completely locked. This produces a pop up on trying to exit.

I'm sure that there is something simple I'm missing, I hope someone wiser than me can help.


TIA STEVE.

---

### Post by singedwings on 2010-05-24
Well done for finding Parker1's guide as it is the best I know of. I would recommend turning on the autobuilds-fixes from mythbuntu's site [http://www.mythbuntu.org/auto-builds]("http://www.mythbuntu.org/auto-builds") things seem to get fixed and broken all the time in myth.

You state that you have a dvb-s card so you should not need to set any dvb-t settings. I would suggest with your setup that you should set the simultanious jobs to a max of 2 in the capture card - recording options.

If I followed Parker's instructions for the channel scanning and used a channels.conf I found that I would get the channels but no EIT, since myth 0.22. So this is how I do it (and I have just noticed that Parker has updated his guide as well):-

In input connections - scan for channels. Assuming you are scanning on the Sky/Freesat Astra Satellite. Set the frequency to 10714000, Horizontal, 22000000 and run a full scan. This manually adds the channel 4 transport and the full scan searches and adds the rest automatically. It may crash but stick with it it will work eventually. You then have to add the channels it has found, for the conflicts click suggest and basically add the channels it suggests a number above 1000 and cancel the rest of them. Careful not to click cancel all as you will have to start all over again! Set the starting channel to something that should work like Sky News 4704.

Also I have found that the EIT guide for some reason does not work for the channel 4 transport that I added manually to start the scan. So in the channel editor - edit transports and delete the ones that look different at the top of the list. Then in input connections run another scan of existing transports with the search for new transports option checked.

Phew, good luck!

---

### Post by bance on 2010-05-25
@Sidewings,

Thanks for the reply,

Actually the card I have is a quad mode card, dvb-t,dvb-s,dvb-s1,and radio!

I did persist and eventually succeeded in getting a scan to complete:guitar:

So now I have something to watch, except when I start frontend I get the adapters are busy message! I think I'll be able to get around that because I've seen posts with this problem and there's a fix.

Thanks for your input,

Steve.

---

