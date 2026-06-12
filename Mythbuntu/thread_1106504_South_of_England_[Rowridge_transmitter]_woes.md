---
title: "South of England [Rowridge transmitter] woes"
date: 2009-03-25
forum: Mythbuntu
---

### Post by smbm on 2009-03-25
Hi

Our local transmitter was re-jigged today and everything seems to have gone awry.

We've lost the ITVs and the Channel 4 type channels.

Anyone else affected?

Anyone know what I can do to fix?

Got a link to a thread on a Freeview related forum, I don't really understand much of it though! Can anyone help to decode it?

[http://www.digitalspy.co.uk/forums/showthread.php?t=1000054&page=3](http://www.digitalspy.co.uk/forums/showthread.php?t=1000054&page=3)

The posts from the 25th are the relevant ones.

I'm not really up on muxes and what have you.

Thanks very much in advance.

---

### Post by SiHa on 2009-03-26
I'm in Southampton, and also get my signal from Rowridge.

First, you'll need to re-scan in the backend setup. I deleted and re-created the video source, but you may be able to just go into it and re-scan. Also I found one of the tuner cards was erroring, don't know if it was a result of switchiver, I had to go back into the capture card setup so re-detect the card.
Once you've scanned, you will find that all the programs are mixed up with strange channel numbers. You can change these manually in the channel editor, or try this post:
[http://ubuntuforums.org/showthread.php?t=914136](http://ubuntuforums.org/showthread.php?t=914136)
Beware, that I haven't tried it myself, and also some of the channel names have changed since the above post.
Myself, I just turned on the TV, which has DVB built in, and wrote down the channel number for each channel and edited them manually in the channel editor.
Now all I've got to do is find out why CH5 has no EIT EPG info. I'd be interested to know what you have for CH5??

---

### Post by smbm on 2009-03-26
That seemed to do the trick. I was just rescanning the channels which didn't appear to be good enough.

I have full data for ch5, how odd.

BBC3's data still hasn't populated itself in mythweb for me though so maybe it just takes a while to adjust.

I'm in Southampton too, do you know if we have a LUG or anything?

---

### Post by SiHa on 2009-03-26
> **smbm said:**
> I'm in Southampton too, do you know if we have a LUG or anything?

Don't know, I'm afraid. Still quite new to the whole Linux thing...

Still no Chan 5 EPG. Maybe I'll try another mythfilldatabase run.

---

### Post by Crowie on 2009-03-27
your lucky, in chandlers ford some of us have no channels.  Did have bbc for a while yesterday but nothing today, also tried with built in freeview on the tv :(

there is a hampshire LUG although ive not yet joined

[http://www.hants.lug.org.uk/cgi-bin/wiki.pl](http://www.hants.lug.org.uk/cgi-bin/wiki.pl)

and the bbc link

[http://news.bbc.co.uk/1/hi/england/7965639.stm](http://news.bbc.co.uk/1/hi/england/7965639.stm)

---

### Post by Slate8 on 2009-03-27
Am in the south too and had BBC disappearing recently. A rescan in the backend seems to have solved things, I didn't need to remove and re-create sources. Here's another post that may help with ordering the channels correctly after a rescan. [http://ubuntuforums.org/showthread.php?t=497488]("http://ubuntuforums.org/showthread.php?t=497488")

---

### Post by Crowie on 2009-03-28
lol freeview works in the bedroom off set-top box (good signal too) but not the front room.  Im in a fairly new build, so either its running off two separate aerials or the wirings pretty poor when they put these places up.

ive swapped the combi FE/BE box in lounge for the FE in bedroom for the time being and feed it the signal that way. :( was enjoying VDPAU aswell.

---

### Post by J566 on 2009-03-28
I live in Hedge End and since the re-tune on Wednesday 25th my myth box refuses to show any channels from Multilplex 2 (ITV, Channel4 etc) and also CBeebies. The channels appear to tune ok and show in the guide including guide data but refuse to get a channel lock when you select them. My cheap £20 sagem box in the bedroom gets all channels no problem. I also have a WindowsXP machine with a Leadtek Gold dongle and since the re-tune that has lost all the BBC channels but can get all the ITV and Channel4 channels. I'm stumped as to what to do apart from doing a daily retune to see if anything changes. Reading various forum posts though a number of other myth users are having the same trouble with the MUX2 ITV channels and also people with PVR set top boxes from the likes of Humax etc. So I don't think spending money on a new STB will necessarily solve my problem. Don't want to pour more money down the drain. Maybe abandon freeview and try freesat.

---

### Post by smbm on 2009-03-28
That's exactly what I had until I deleted all card related config, added them again and re-scanned. Now everything is pretty much hunky dory.

---

### Post by Crowie on 2009-03-28
yes I had to reinstall my card related config after moving my FE/BE combi to the bedroom.
All my neighbours freeview in our block is the same (works in bedroom but broken in the lounge), turns out we had an engineer round on thursday to boost the signal and he messed it up.

but thanks to mythtv I can feed it through the homeplugs to another FE

---

### Post by Jose Catre-Vandis on 2009-03-28
I don't use mythtv ( I use mplayer for all my Linux TV needs) but did get a cracking signal from Rowridge, on a normal aerial, from North of Winchester! Now the signal has gone completely. I cannot even scan for channels. Fortunately for me, I am able to turn my aerial around 180 degrees and use Hannington. The signal seems to have improved a bit since last used on my linux box. It's always been OK on the real TV but a bit blocky on the PC.

What is most annoying is that Digital UK issued absolutely no information for linux dvb-t tuning

---

### Post by J566 on 2009-03-28
Just gone and deleted all the card and connection information and put it back in from scratch and everything is happy here again now. Thanks.

---

### Post by J566 on 2009-03-28
> **Jose Catre-Vandis said:**
> 

What is most annoying is that Digital UK issued absolutely no information for linux dvb-t tuning

There seems to be no information from Digital UK that there is a problem or technical information as to why a simple re-scan is not working for a large number of people.

I now have mythtv working again under linux but yet to try and get the leadtek dongle working under windows other than numerous rescans which is as technical as the software allows without totally uninstalling the drivers and starting again - I'll try that later. These cards are not legacy cards that are now incompatible they are currently on sale. Indeed I only recently purchased the leadtek dongle so I don't see that it shouldn't find everything with a simple re-scan. If my sagem freeview box that is much older than the PC based cards had no trouble and all the PC cards worked fine prior to the re-jig on the 25th then that suggests that the changes were much more fundamental than they are letting on. It seems digital uk should offer more information and advice as to what has technically changed and why it is not a simple rescan for a lot of people. They are just churning out the upgrade your aerial or rescan. My aerial was professionally installed a couple of years ago.

Rant over... sorry :)

---

### Post by Keithamus on 2009-04-02
This for me is still a very real problem! I have lost Multiplex2, which serves up most of Channel4 (Ch4, +1, E4) as well as ITV. It is incredibly frustrating. The method of deleting all of the info in mythtv-setup and reconfiguring seems to leave me with a broken backend... saying that the tuner is busy (although the settings are identical). What are the freqids for everyone elses setup?

I have scanned many times. I have called the Rowridge area helpline, and they just tell me to rescan!

I encourage everyone with problems to pester them - the number is 0845 845 0231. Also, complain to Ofcom if you are dissatisfied with the services provided! I know I will be.

EDIT-
PS When I try to switch to any channel in mux 2, I get the lock letters "La", other channels, as expected, say "LAM". According to the mythtv guide, this means it cant see any mpeg2 streams on that channel.

---

### Post by smbm on 2009-04-02
I had to do a hard reset to unload/reload the firmware for my card too.

Have you tried that?

---

### Post by Keithamus on 2009-04-03
I wouldn't know where to begin with unloading/reloading firmware on a pci device in linux...

It seems like an utterly crazy thing to have to do for a simple retune... but uh, got any references i can read to learn how to do it? (My card is a Hauppauge Nova T 500)

---

### Post by smbm on 2009-04-03
> **Keithamus said:**
> I wouldn't know where to begin with unloading/reloading firmware on a pci device in linux...

It seems like an utterly crazy thing to have to do for a simple retune... but uh, got any references i can read to learn how to do it? (My card is a Hauppauge Nova T 500)

I have the same card :p

All you have to do is power down the computer (ie turn it off, a restart without turning the power off won't do it, I also pulled the power lead for about 10 secs just for good measure) and turn it on again to reload the firmware.

The firmware is loaded at boot by the kernel and I believe stays until a power cycle so that should do the trick.

Good luck, let me know how you get on.

---

### Post by Keithamus on 2009-04-03
While waiting for a reply, I googled around a bit and found that the actual firmware file I was using was outdated:

```

$ ls /lib/firmware/dvb-usb-dib0700-*
dvb-usb-dib0700-1.10.fw

```

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500) this website suggests moving to 1.20.fw, and supplies a link. So I did this:

```

$ wget http://www.wi-bw.tfh-wildau.de/~pboettch/home/files/dvb-usb-dib0700-1.20.fw
$ sudo mv dvb-usb-dib0700-1.20.fw /lib/firmware/
$ ls /lib/firmware/dvb-usb-dib0700-*
dvb-usb-dib0700-1.10.fw dvb-usb-dib0700-1.20.fw

```

After this I read your post and powered down. Mux 2 still doesn't work. Do I need to rescan? Aso, the 1.20 fw hasn't loaded:

```

$ dmesg | grep -i firmware
[   13.153151] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   13.153155] firmware: requesting dvb-usb-dib0700-1.10.fw
[   14.364831] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   14.571525] dib0700: firmware started successfully

```

Is there a way to load the new firmware? Do I need to delete the old firmware? Are you using version 1.10 or 1.20?

---

### Post by smbm on 2009-04-03
I'm not sure about the firmware issue, I'm of the if it ain't broke don't upgrade the firmware school of thought (although yours is broken so maybe it will help). Alas I've no skills in that department though.

I completely deleted my cards from the myth backend and then did the power down/power up then re-added the cards and rescanned this did the trick for me. 

I think the most important thing was deleting the cards and re-adding them, it was all guesswork though so I could be wrong.

---

### Post by Keithamus on 2009-04-03
Ok, I did everything you said, but my card is broken like before...

Here is everything I can think of to help.

--EDIT-- Noticed it said "warm state" so I hard reset again until it said "cold state", but still no luck...
```

$ dmesg | grep -i dvb
[   12.145017] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   12.145022] firmware: requesting dvb-usb-dib0700-1.10.fw
[   13.497857] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   14.204044] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   14.204171] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.835330] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.452185] dvb-usb: schedule remote query interval to 150 msecs.
[   15.452191] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   15.452473] usbcore: registered new interface driver dvb_usb_dib0700

```

```

$ mythbackend -d >> log.txt
$ cat log.txt
2009-04-03 20:42:31.026 Using runtime prefix = /usr
2009-04-03 20:42:31.027 Empty LocalHostName.
2009-04-03 20:42:31.027 Using localhost value of cerberus
2009-04-03 20:42:31.034 New DB connection, total: 1
2009-04-03 20:42:31.038 Connected to database 'mythconverg' at host: localhost
2009-04-03 20:42:31.038 Closing DB connection named 'DBManager0'
2009-04-03 20:42:31.039 Connected to database 'mythconverg' at host: localhost
2009-04-03 20:42:31.040 New DB connection, total: 2
2009-04-03 20:42:31.040 Connected to database 'mythconverg' at host: localhost
2009-04-03 20:42:31.041 Current Schema Version: 1214
2009-04-03 20:42:31.187 New DB connection, total: 3
2009-04-03 20:42:31.187 Connected to database 'mythconverg' at host: localhost
2009-04-03 20:42:31.580 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-04-03 20:42:31.590 ChannelBase(2) Error: InitializeInputs():
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?

```

```

$ cat .mythtv/Default.xmltv
encoding=utf-8
cachedir=/home/pundit/.xmltv/cache
title-processing=enabled
postcode=#CENSORED#
platform=freeview
channel=4music.channel4.com
channel=bbcfour.bbc.co.uk
channel=news.bbc.co.uk
channel=south.bbc1.bbc.co.uk
channel=parliament.bbc.co.uk
channel=interactive.sport.bbc.co.uk
channel=bbcthree.bbc.co.uk
channel=south.bbc2.bbc.co.uk
channel=bid.tv
channel=cbbc.bbc.co.uk
channel=cbeebies.bbc.co.uk
channel=channel4.com
channel=tsod.plus-1.channel4.com
channel=citv.itv.co.uk
channel=freeview.europe.cnn.com
channel=freeview.communitychannel.org
channel=dave.uktv.co.uk
channel=tsod.plus-1.dave.uktv.co.uk
channel=e4.channel4.com
channel=tsod.plus-1.e4.channel4.com
channel=filmfour.channel4.com
channel=channel5.co.uk
channel=fiveusa.channel5.co.uk
channel=fiver.channel5.co.uk
channel=idealworld.tv
channel=meridian.itv1.itv.co.uk
channel=itv2.itv.co.uk
channel=tsod.plus-1.itv2.itv.co.uk
channel=itv3.itv.co.uk
channel=itv4.itv.co.uk
channel=more4.channel4.com
channel=qvcuk.com
channel=sky-news.sky.com
channel=news.sports.sky.com
channel=sky-three.sky.com
channel=dvb.teachers.tv
channel=tmf.nl
channel=freeview.1.virginmedia.com
channel=freeview.yesterday.uktv.co.uk

```

If this helps at all, these are my relevant SQL tables:

```

mysql> SELECT * FROM capturecard;
+--------+-------------+-------------+-----------+----------+--------------+----------------+----------+--------------+--------------+-----------------------+-------------+---------------+-----------------+----------------+----------------+---------------------+------------+----------------+------------+----------------+-----------------+------------------+----------+------------+--------+-----+----------+-------------+
| cardid | videodevice | audiodevice | vbidevice | cardtype | defaultinput | audioratelimit | hostname | dvb_swfilter | dvb_sat_type | dvb_wait_for_seqstart | skipbtaudio | dvb_on_demand | dvb_diseqc_type | firewire_speed | firewire_model | firewire_connection | dbox2_port | dbox2_httpport | dbox2_host | signal_timeout | channel_timeout | dvb_tuning_delay | contrast | brightness | colour | hue | diseqcid | dvb_eitscan |
+--------+-------------+-------------+-----------+----------+--------------+----------------+----------+--------------+--------------+-----------------------+-------------+---------------+-----------------+----------------+----------------+---------------------+------------+----------------+------------+----------------+-----------------+------------------+----------+------------+--------+-----+----------+-------------+
|      1 | 0           |             |           | DVB      | DVBInput     |           NULL | cerberus |            0 |            0 |                     1 |           0 |             1 |            NULL |              0 | NULL           |                   0 |      31338 |             80 | NULL       |            500 |            3000 |               25 |        0 |          0 |      0 |   0 |        0 |           0 |
|      2 | 0           | NULL        | NULL      | DVB      | DVBInput     |           NULL | cerberus |            0 |            0 |                     1 |           0 |             1 |               0 |              0 | NULL           |                   0 |      31338 |             80 | NULL       |            500 |            3000 |               25 |        0 |          0 |      0 |   0 |        0 |           0 |
|      3 | 1           |             |           | DVB      | DVBInput     |           NULL | cerberus |            0 |            0 |                     1 |           0 |             1 |            NULL |              0 | NULL           |                   0 |      31338 |             80 | NULL       |            500 |            3000 |               25 |        0 |          0 |      0 |   0 |        0 |           0 |
|      4 | 1           | NULL        | NULL      | DVB      | DVBInput     |           NULL | cerberus |            0 |            0 |                     1 |           0 |             1 |               0 |              0 | NULL           |                   0 |      31338 |             80 | NULL       |            500 |            3000 |               25 |        0 |          0 |      0 |   0 |        0 |           0 |
+--------+-------------+-------------+-----------+----------+--------------+----------------+----------+--------------+--------------+-----------------------+-------------+---------------+-----------------+----------------+----------------+---------------------+------------+----------------+------------+----------------+-----------------+------------------+----------+------------+--------+-----+----------+-------------+
4 rows in set (0.00 sec)

```

```

mysql> SELECT * FROM cardinput;
+-------------+--------+----------+-----------+-----------------+-----------+----------+-----------+---------------+-------------+---------------+-------------+-------------+-----------+
| cardinputid | cardid | sourceid | inputname | externalcommand | shareable | tunechan | startchan | freetoaironly | displayname | radioservices | dishnet_eit | recpriority | quicktune |
+-------------+--------+----------+-----------+-----------------+-----------+----------+-----------+---------------+-------------+---------------+-------------+-------------+-----------+
|           1 |      1 |        1 | DVBInput  | NULL            | N         | NULL     | 1         |             1 | Tuner 1     |             1 |           0 |           0 |         1 |
|           2 |      3 |        1 | DVBInput  | NULL            | N         | NULL     | 1         |             1 | Tuner 2     |             1 |           0 |           0 |         1 |
+-------------+--------+----------+-----------+-----------------+-----------+----------+-----------+---------------+-------------+---------------+-------------+-------------+-----------+
2 rows in set (0.00 sec)

```

```

mysql> SELECT * FROM dtv_multiplex;
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
| mplexid | sourceid | transportid | networkid | frequency | inversion | symbolrate | fec  | polarity | modulation | bandwidth | lp_code_rate | transmission_mode | guard_interval | visible | constellation | hierarchy | hp_code_rate | sistandard | serviceversion | updatetimestamp     |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
|       1 |        1 |       24576 |      9018 | 570166670 | a         |       NULL | NULL | NULL     | NULL       | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | dvb        |              0 | 2009-04-03 19:28:37 |
|       2 |        1 |        4099 |      9018 | 578166670 | a         |       NULL | NULL | NULL     | NULL       | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | dvb        |              1 | 2009-04-03 19:28:53 |
|       3 |        1 |        8206 |      9018 | 562000000 | a         |       NULL | NULL | NULL     | NULL       | 8         | 1/2          | 2                 | 1/32           |       0 | qam_64        | n         | 2/3          | dvb        |              0 | 2009-04-03 19:28:42 |
|       4 |        1 |       12290 |      9018 | 545833330 | a         |       NULL | NULL | NULL     | NULL       | 8         | 1/2          | 2                 | 1/32           |       0 | qam_64        | n         | 2/3          | dvb        |              2 | 2009-04-03 19:28:33 |
|       5 |        1 |       16384 |      9018 | 530000000 | a         |       NULL | NULL | NULL     | NULL       | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | dvb        |             15 | 2009-04-03 19:28:23 |
|       6 |        1 |       20480 |      9018 | 602000000 | a         |          0 | auto | v        | qam_16     | 8         | 1/2          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | dvb        |             15 | 2009-04-03 19:28:58 |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
6 rows in set (0.05 sec)

```

More stuff from googling around for stuff:

```

$ lsof /dev/dvb/adapter0/frontend0
$
$ lsof /dev/dvb/adapter1/frontend0
$
$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Rowridge > .tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Rowridge
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

```

---

### Post by Keithamus on 2009-04-03
Something really interesting; I installed Kaffeine, which is a compatible DVB player. It tunes to all of my channels fine. It says "device or resource busy" for tuner 1, but will tune in using tuner 2. It also tunes to channel 4! (And as such I presume tunes into the rest of the mux).

So, its a mythbackend problem I presume. Has anyone come across this before?

I am using the VDPAU patches repository supplied here (the stable branch):
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)
which does modify the mythbackend, but I cannot beleive it modifies it enough to break DVB tuning.

P.S

As this is no longer a rowridge retune issue shall I stop hijacking this thread and make a new topic :D?

---

### Post by megs on 2009-07-27
Probably unrelated, but might help someone else.  I'm in Eastleigh, and myth hadn't worked properly since the swap over.  Yesterday I finally got around to doing something about it, deleting cards, muxes, all sorts.  When I finally convinced it to do a rescan, it set a frequency of 0 for 2 of the muxes.  I got the right values from a post earlier in this thread, and reset them using phpmyadmin in the dtv-multiplex table.  Sorted.

---

### Post by megs on 2009-07-27
> **Keithamus said:**
> Ok, I did everything you said, but my card is broken like before...

Here is everything I can think of to help.


CHOPPING FOR BREVITY...

```

mysql> SELECT * FROM dtv_multiplex;
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
| mplexid | sourceid | transportid | networkid | frequency | inversion | symbolrate | fec  | polarity | modulation | bandwidth | lp_code_rate | transmission_mode | guard_interval | visible | constellation | hierarchy | hp_code_rate | sistandard | serviceversion | updatetimestamp     |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
|       1 |        1 |       24576 |      9018 | 570166670 | a         |       NULL | NULL | NULL     | NULL       | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | dvb        |              0 | 2009-04-03 19:28:37 |
|       2 |        1 |        4099 |      9018 | 578166670 | a         |       NULL | NULL | NULL     | NULL       | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | dvb        |              1 | 2009-04-03 19:28:53 |
|       3 |        1 |        8206 |      9018 | 562000000 | a         |       NULL | NULL | NULL     | NULL       | 8         | 1/2          | 2                 | 1/32           |       0 | qam_64        | n         | 2/3          | dvb        |              0 | 2009-04-03 19:28:42 |
|       4 |        1 |       12290 |      9018 | 545833330 | a         |       NULL | NULL | NULL     | NULL       | 8         | 1/2          | 2                 | 1/32           |       0 | qam_64        | n         | 2/3          | dvb        |              2 | 2009-04-03 19:28:33 |
|       5 |        1 |       16384 |      9018 | 530000000 | a         |       NULL | NULL | NULL     | NULL       | 8         | 3/4          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | dvb        |             15 | 2009-04-03 19:28:23 |
|       6 |        1 |       20480 |      9018 | 602000000 | a         |          0 | auto | v        | qam_16     | 8         | 1/2          | 2                 | 1/32           |       0 | qam_16        | n         | 3/4          | dvb        |             15 | 2009-04-03 19:28:58 |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+------------+----------------+---------------------+
6 rows in set (0.05 sec)

```


It was transport ID's 8206 and 16384 (the first one carries ITV, not sure about the second) that needed their frequencies adjusting.  The error message in the /var/log/mythtv/mythbackend.log that gave me a clue was 
DVBChan(1:0) Warning: Your frequency setting (0) is out of range. (min/max:44250000/867250000)
Then, having installed phpmyadmin previously, I was able to go and edit the tables manually, not sure if there's a cleaner way of doing it - but what's life without a risk here and there?
Megs

---

