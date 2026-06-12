---
title: "Mythbackend &quot;Device or resource busy&quot;, Kaffiene works though"
date: 2009-04-04
forum: Mythbuntu
---

### Post by Keithamus on 2009-04-04
I have issues with my mythbackend. I re-set-up all of my tuners and channels because the local (Rowridge) transmitter retune was causing me jip. Now mythbackend won't load, complaining about the DVB card being busy.

I've already posted this in a separate thread - but figured it is best off on its own, being a separate issue. Here is all the logs and outputs I can think of that may help:

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

```

mysql> SELECT * FROM inputgroup;
+-------------+--------------+----------------+
| cardinputid | inputgroupid | inputgroupname |
+-------------+--------------+----------------+
|           1 |            1 | DVB0           |
|           2 |            2 | DVB1           |
+-------------+--------------+----------------+
2 rows in set (0.00 sec)

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


As I stated in the other thread - Kaffeine works fine to scan and playback all my freeview channels - where Mythbackend bluntly refuses to. It was working pre-march 25th (when the Rowridge transmitter was retuned).

Please help! WAF has dropped exponentially...

---

### Post by Keithamus on 2009-04-04
I found that the mythbackend service was running, and was locking up the scan command.

However, mythbackend still doesn't work! Everything as far as I can see is fine. It is so frustrating!

---

### Post by Kytsi on 2009-04-05
Hi

So you have mythbackend running?

What mythfrontend says when you try to watch liveTV?

If it says something like "all tuners are in use, bla.bla..."
then the reason is that you have to give rights, for user you are running mythbackend, to use dvb adapters.

---

### Post by Keithamus on 2009-04-05
It says:

```

Could not connect to the master backend server -- is it running? Is the IP address set for it in the setup program correct?

```

In mythtv-setup, Local Backend IP is 127.0.0.1 port 6544. Master backend is 127.0.0.1 port 6543.

---

### Post by Kytsi on 2009-04-06
So you have one backend?

Why you are trying to connect on different ports?

try 127.0.0.1:6543 for both local and master backends.

---

### Post by Keithamus on 2009-04-06
My bad, I misread it. Both are set to 6543, the backend status port is set to 6544.

Checked all of the connections for the 50th time, or what it feels like. Everything looks fine, but the problem still exists:

```

2009-04-06 10:35:39.317 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-04-06 10:35:39.328 ChannelBase(2) Error: InitializeInputs():
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?



```

---

### Post by Kytsi on 2009-04-06
OK so you have mythbackend up and running but mythfrontend is unable to connect to it?

Have checked connection settings of mythfrontend from mythfrontends settings?

Mythbackend error sounds that you have forgotten to bind input source to dvb card.

check this thread [http://ubuntuforums.org/showthread.php?t=1116346]("http://ubuntuforums.org/showthread.php?t=1116346")

---

### Post by Keithamus on 2009-04-06
I was hunting around for a while to find mythfrontends connection settings, but can't seem to find them. Do you know specifically where they are?

As you can see from the mysql select statements above I have set up all the required connections. CaptureCards, VideoSources and InputConnections all have the details that look right to me. I have thoroughly checked these against my old working db (It was working except for one multiplex, which is why I am going through this mess).

Unless you can see anything I have done wrong, as far as I can see, everything is right.

---

### Post by joshoekstra on 2009-04-06
It might be a good idea to create a channel-setup, this says it all:

> 2009-04-06 10:35:39.317 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-04-06 10:35:39.328 ChannelBase(2) Error: InitializeInputs():
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?

You still need to setup a channel lineup(like a xmltv-grabber or eit/epg), with that you fill de myth database with the correct info.

---

### Post by Keithamus on 2009-04-06
This is what I don't get, I actually have a full channel lineup assigned to the "Default" video source, which is assigned to both of my tuners in Input Connections.

If there was a smilie for tearing my hair out, I'd be using it right now.

EDIT- Just to prove my point, here are the corresponding tables:
```

mysql> SELECT * FROM channel LIMIT 10;
+--------+---------+--------+----------+----------------+----------------+-----------------------------------------------------------------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+---------+---------------+---------------+---------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
| chanid | channum | freqid | sourceid | callsign       | name           | icon                                                            | finetune | videofilters | xmltvid | recpriority | contrast | brightness | colour | hue   | tvformat | visible | outputfilters | useonairguide | mplexid | serviceid | tmoffset | atsc_major_chan | atsc_minor_chan | last_record         | default_authority | commmethod |
+--------+---------+--------+----------+----------------+----------------+-----------------------------------------------------------------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+---------+---------------+---------------+---------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
|   1081 | 81      | NULL   |        1 | BBC Parliament | BBC Parliament | /home/pundit/.mythtv//channels/bbc_parliament.jpg               |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     17024 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1071 | 71      | NULL   |        1 | CBeebies       | CBeebies       | /home/pundit/.mythtv//channels/bbc_cbeebies.jpg                 |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     16960 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1705 | 705     | NULL   |        1 | BBC R5L        | BBC R5L        | /home/pundit/.mythtv//channels/bbc_radio5_live.jpg              |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     17920 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1706 | 706     | NULL   |        1 | BBC R5SX       | BBC R5SX       | /home/pundit/.mythtv//channels/bbc_radio5_live_sports_extra.jpg |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     17984 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1707 | 707     | NULL   |        1 | BBC 6 Music    | BBC 6 Music    | /home/pundit/.mythtv//channels/bbc_radio6_music.jpg             |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     18048 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1708 | 708     | NULL   |        1 | BBC Radio 7    | BBC Radio 7    | /home/pundit/.mythtv//channels/bbc_radio7.jpg                   |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     18112 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1701 | 701     | NULL   |        1 | BBC 1Xtra      | BBC 1Xtra      | /home/pundit/.mythtv//channels/bbc_radio1_xtra.jpg              |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     18176 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1709 | 709     | NULL   |        1 | BBC Asian Net. | BBC Asian Net. | /home/pundit/.mythtv//channels/bbc_asian_network.jpg            |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     18240 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1301 | 301     | NULL   |        1 | 301            | 301            | /home/pundit/.mythtv//channels/bbc_i.jpg                        |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     19456 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
|   1302 | 302     | NULL   |        1 | 302            | 302            | /home/pundit/.mythtv//channels/bbc_i.jpg                        |     NULL |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |       5 |     19520 |        0 |               0 |               0 | 0000-00-00 00:00:00 | fp.bbc.co.uk      |         -1 |
+--------+---------+--------+----------+----------------+----------------+-----------------------------------------------------------------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+---------+---------------+---------------+---------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
10 rows in set (0.00 sec)

```

```

mysql> SELECT * FROM videosource;
+----------+---------+---------------+--------+-----------+----------+----------+--------+
| sourceid | name    | xmltvgrabber  | userid | freqtable | lineupid | password | useeit |
+----------+---------+---------------+--------+-----------+----------+----------+--------+
|        1 | Default | tv_grab_uk_rt |        | try-all   | NULL     | NULL     |      1 |
+----------+---------+---------------+--------+-----------+----------+----------+--------+
1 row in set (0.00 sec)

```

```

mysql> SELECT * FROM inputgroup;
+-------------+--------------+----------------+
| cardinputid | inputgroupid | inputgroupname |
+-------------+--------------+----------------+
|           1 |            1 | DVB0           |
|           2 |            2 | DVB1           |
+-------------+--------------+----------------+
2 rows in set (0.04 sec)

```

```

mysql> SELECT * FROM capturecard;
+--------+-----------------------------+-------------+-----------+----------+--------------+----------------+----------+--------------+--------------+-----------------------+-------------+---------------+-----------------+----------------+----------------+---------------------+------------+----------------+------------+----------------+-----------------+------------------+----------+------------+--------+-----+----------+-------------+
| cardid | videodevice                 | audiodevice | vbidevice | cardtype | defaultinput | audioratelimit | hostname | dvb_swfilter | dvb_sat_type | dvb_wait_for_seqstart | skipbtaudio | dvb_on_demand | dvb_diseqc_type | firewire_speed | firewire_model | firewire_connection | dbox2_port | dbox2_httpport | dbox2_host | signal_timeout | channel_timeout | dvb_tuning_delay | contrast | brightness | colour | hue | diseqcid | dvb_eitscan |
+--------+-----------------------------+-------------+-----------+----------+--------------+----------------+----------+--------------+--------------+-----------------------+-------------+---------------+-----------------+----------------+----------------+---------------------+------------+----------------+------------+----------------+-----------------+------------------+----------+------------+--------+-----+----------+-------------+
|      1 | /dev/dvb/adapter0/frontend0 |             |           | DVB      | DVBInput     |           NULL | cerberus |            0 |            0 |                     1 |           0 |             1 |            NULL |              0 | NULL           |                   0 |      31338 |             80 | NULL       |            500 |            3000 |               25 |        0 |          0 |      0 |   0 |        0 |           0 |
|      2 | /dev/dvb/adapter0/frontend0 | NULL        | NULL      | DVB      | DVBInput     |           NULL | cerberus |            0 |            0 |                     1 |           0 |             1 |               0 |              0 | NULL           |                   0 |      31338 |             80 | NULL       |            500 |            3000 |               25 |        0 |          0 |      0 |   0 |        0 |           0 |
|      3 | /dev/dvb/adapter1/frontend0 |             |           | DVB      | DVBInput     |           NULL | cerberus |            0 |            0 |                     1 |           0 |             1 |            NULL |              0 | NULL           |                   0 |      31338 |             80 | NULL       |            500 |            3000 |               25 |        0 |          0 |      0 |   0 |        0 |           0 |
|      4 | /dev/dvb/adapter1/frontend0 | NULL        | NULL      | DVB      | DVBInput     |           NULL | cerberus |            0 |            0 |                     1 |           0 |             1 |               0 |              0 | NULL           |                   0 |      31338 |             80 | NULL       |            500 |            3000 |               25 |        0 |          0 |      0 |   0 |        0 |           0 |
+--------+-----------------------------+-------------+-----------+----------+--------------+----------------+----------+--------------+--------------+-----------------------+-------------+---------------+-----------------+----------------+----------------+---------------------+------------+----------------+------------+----------------+-----------------+------------------+----------+------------+--------+-----+----------+-------------+
4 rows in set (0.00 sec)

```

---

### Post by joshoekstra on 2009-04-06
Hmmm, as far as I can see(normally using the backend-setup-options instead of mysql output) you seem to be having the right settings, did you try another starting-channel like 81, 71 or something?
A tail -f /var/log/messages might provide some insight as well as lsof | grep /dev/dvb might.
After that I'm out of ideas other than completely re-running the backend-setup where you first delete all capturecards...

---

### Post by Keithamus on 2009-04-06
```

$ tail -f /var/log/messages
Apr  6 21:02:27 cerberus syslogd 1.5.0#2ubuntu6: restart.

```

```

$ lsof | grep /dev/dvb/
kaffeine  11287     pundit   12u      CHR              212,3               13697 /dev/dvb/adapter0/frontend0
kaffeine  11287     pundit   13r      CHR              212,5               13664 /dev/dvb/adapter0/dvr0
kaffeine  11287     pundit   14u      CHR              212,4               13673 /dev/dvb/adapter0/demux0
kaffeine  11287     pundit   15u      CHR              212,4               13673 /dev/dvb/adapter0/demux0
kaffeine  11287     pundit   16u      CHR              212,4               13673 /dev/dvb/adapter0/demux0
kaffeine  11287     pundit   17u      CHR              212,4               13673 /dev/dvb/adapter0/demux0
kaffeine  11287     pundit   19u      CHR              212,4               13673 /dev/dvb/adapter0/demux0

```

At the moment, I am watching TV using Kaffeine. Obviously without Kaffeine it still comes up with the errors!

I ran mythbackend with and without kaffeine running, this is the log for each:

Without Kaffeine:
```

$ mythbackend
2009-04-06 21:12:20.609 Using runtime prefix = /usr
2009-04-06 21:12:20.620 Empty LocalHostName.
2009-04-06 21:12:20.620 Using localhost value of cerberus
2009-04-06 21:12:20.677 New DB connection, total: 1
2009-04-06 21:12:20.681 Connected to database 'mythconverg' at host: 127.0.0.1
2009-04-06 21:12:20.682 Closing DB connection named 'DBManager0'
2009-04-06 21:12:20.682 Connected to database 'mythconverg' at host: 127.0.0.1
2009-04-06 21:12:20.683 New DB connection, total: 2
2009-04-06 21:12:20.684 Connected to database 'mythconverg' at host: 127.0.0.1
2009-04-06 21:12:20.686 Current Schema Version: 1214
Starting up as the master server.
2009-04-06 21:12:20.844 New DB connection, total: 3
2009-04-06 21:12:20.845 Connected to database 'mythconverg' at host: 127.0.0.1
2009-04-06 21:12:21.247 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-04-06 21:12:21.257 ChannelBase(2) Error: InitializeInputs():
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?

```

With Kaffeine running
```

$ mythbackend
2009-04-06 21:12:53.349 Using runtime prefix = /usr
2009-04-06 21:12:53.350 Empty LocalHostName.
2009-04-06 21:12:53.350 Using localhost value of cerberus
2009-04-06 21:12:53.357 New DB connection, total: 1
2009-04-06 21:12:53.361 Connected to database 'mythconverg' at host: 127.0.0.1
2009-04-06 21:12:53.361 Closing DB connection named 'DBManager0'
2009-04-06 21:12:53.362 Connected to database 'mythconverg' at host: 127.0.0.1
2009-04-06 21:12:53.363 New DB connection, total: 2
2009-04-06 21:12:53.364 Connected to database 'mythconverg' at host: 127.0.0.1
2009-04-06 21:12:53.365 Current Schema Version: 1214
Starting up as the master server.
2009-04-06 21:12:53.371 DVBChan(1:0) Error: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2009-04-06 21:12:53.372 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-04-06 21:12:53.372 DVBChan(2:0) Error: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2009-04-06 21:12:53.373 DVBChan(3:0) Error: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2009-04-06 21:12:53.374 TVRec(4) Error: Problem finding starting channel, setting to default of '3'.
2009-04-06 21:12:53.374 DVBChan(4:0) Error: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-04-06 21:12:53.386 New DB connection, total: 3
2009-04-06 21:12:53.387 Connected to database 'mythconverg' at host: 127.0.0.1
2009-04-06 21:12:53.403 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-04-06 21:12:53.403 Main::Registering HttpStatus Extension
2009-04-06 21:12:53.403 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-04-06 21:12:53.403 Enabled verbose msgs:  important general
2009-04-06 21:12:53.405 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-04-06 21:12:55.989 MainServer::HandleAnnounce Monitor
2009-04-06 21:12:55.989 adding: cerberus as a client (events: 0)

```

Something I observed: when Kaffeine wasnt running, the backend effectively was not "running"; I tried to connect to mythweb and got a failed to connect to backend error. With Kaffeine running, I seem to be able to connect to mythweb fine... I guess this is something to do with the way the backend handles the tuner - if it isnt busy and it can't connect to the tuner it is fatal, if the tuner is busy, it ignores it and continues on.

---

### Post by joshoekstra on 2009-04-06
The last part of your logs gave me another idea: does the backend user(probably not the same as you're running kaffeïne with) have rights to use the tuner? It might be that the backend-user needs to be added to the video-group.

---

### Post by Keithamus on 2009-04-06
The setup was working fine a week ago. I deleted the mythtv-setup entries due to a retune of our local transmitter. Since then it has failed to work - so I guess it isn't a permissions issue.

How would I check though?

---

### Post by Keithamus on 2009-04-07
Never mind, I just wiped my install and installed Jaunty Beta. Channels work fine, so now it is just a case of working out my other issues :D

---

