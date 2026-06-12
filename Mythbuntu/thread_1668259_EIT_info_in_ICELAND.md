---
title: "EIT info in ICELAND"
date: 2011-01-16
forum: Mythbuntu
---

### Post by hafthor on 2011-01-16
Hi all 
I am trying to get EIT to stick to my channels in Mythtv without Success.

I started by makeing a Channel.conf and then inserting that, deleteing all the channels and then makeing myth manually scan from existing transports.

What I have done so far is to play around with dvbsnoop and gotten some data

___________________________________________________________________


PID:  18 (0x0012)  [= assigned for: DVB Event Information Table (EIT)]

Guess table from table id...
EIT-decoding....
Table_ID: 80 (0x50)  [= Event Information Table (EIT) - actual transport stream, schedule]
section_syntax_indicator: 1 (0x01)
reserved_1: 1 (0x01)
reserved_2: 3 (0x03)
Section_length: 192 (0x00c0)
Service_ID: 30 (0x001e)  [=  --> refers to PMT program_number]
reserved_3: 3 (0x03)
Version_number: 29 (0x1d)
current_next_indicator: 1 (0x01)  [= valid now]
Section_number: 3 (0x03)
Last_Section_number: 163 (0xa3)
Transport_stream_ID: 33 (0x0021)
Original_network_ID: 100 (0x0064)  [= >>ERROR: not (yet) defined... Report!<<]
Segment_last_Section_number: 10 (0x0a)
Last_table_id: 81 (0x51)  [= Event Information Table (EIT) - actual transport stream, schedule]

    Event_ID: 25225 (0x6289)
    Start_time: 0xd919051000 [= 2011-01-16 05:10:00 (UTC)]
    Duration: 0x0004500 [=  00:45:00 (UTC)]
    Running_status: 0 (0x00)  [= undefined]
    Free_CA_mode: 1 (0x01)  [= streams [partially] CA controlled]
    Descriptors_loop_length: 165 (0xa5)

            DVB-DescriptorTag: 77 (0x4d)  [= short_event_descriptor]
            descriptor_length: 163 (0xa3)
              0000:  4d a3 69 73 6c 0d 10 00  01 45 54 20 57 65 65 6b   M.isl....ET Week
              0010:  65 6e 64 91 10 00 01 46  72 65 6d 73 74 69 20 6f   end....Fremsti o
              0020:  67 20 66 72 e6 67 61 73  74 69 20 fe e1 74 74 75   g fr.gasti ..ttu
              0030:  72 20 ed 20 68 65 69 6d  69 20 fe 61 72 20 73 65   r . heimi .ar se
              0040:  6d 20 61 6c 6c 74 20 fe  61 f0 20 68 65 6c 73 74   m allt .a. helst
              0050:  61 20 73 65 6d 20 67 65  72 f0 69 73 74 20 ed 20   a sem ger.ist .
              0060:  76 69 6b 75 6e 6e 69 20  ed 20 68 65 69 6d 69 20   vikunni . heimi
              0070:  66 ed 6e 61 20 6f 67 20  66 72 e6 67 61 20 66 f3   f.na og fr.ga f.
              0080:  6c 6b 73 69 6e 73 20 65  72 20 74 ed 75 6e 64 61   lksins er t.unda
              0090:  f0 20 e1 20 68 72 65 73  73 69 6c 65 67 61 6e 20   . . hressilegan
              00a0:  68 e1 74 74 2e                                     h.tt.
              ISO639_2_language_code:  isl
            event_name_length: 13 (0x0d)
            event_name: "..ET Weekend"  -- Charset: ISO/IEC 8859  special table
            text_length: 145 (0x91)
            text_char: "..Fremsti og fr&#9618;gasti &#9618;&#9618;ttur &#9618; heimi &#9618;ar sem allt &#9618;a&#9618; helsta sem ger&#9618;ist &#9618; vikunni &#9618; heimi f&#9618;na og fr&#9618;ga f&#9618;lksins er t&#9618;unda&#9618; &#9618; hressilegan h&#9618;tt."  -- Charset: ISO/IEC 8859  special table


-------------------------------------------------------------------------------------------


Also I have set the transport_id network_id and service_id for my open channels, and found data in the DVB snoop that seams to match it.

here is some Mysql info

select chanid, useonairguide from channel, dtv_multiplex
    ->   where serviceid=1 and networkid=100 and transportid=33
    ->     and channel.mplexid=dtv_multiplex.mplexid;
+--------+---------------+
| chanid | useonairguide |
+--------+---------------+
|   8001 |             1 |
+--------+---------------+
1 row in set (0.00 sec)


mysql> select chanid, useonairguide from channel, dtv_multiplex   where serviceid=2 and networkid=100 and transportid=33     and channel.mplexid=dtv_multiplex.mplexid;
+--------+---------------+
| chanid | useonairguide |
+--------+---------------+
|   8002 |             1 |
+--------+---------------+
1 row in set (0.00 sec)


here is my mythtv version 

 mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version   : v0.25pre-865-g3526655
MythTV Branch    : master
Network Protocol : 64
Library API      : 0.25.20110103-1
QT Version       : 4.6.2
Options compiled in:
 linux debug use_hidesyms using_alsa using_jack using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_directfb using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg




What can I do more ? 
I see that 
atsc_major_chan=xx and atsc_minor_chan=yy

are all 0 but I dont know what data I should include in this


I also did this

Database changed
mysql> select * from `dtv_multiplex`;
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
| mplexid | sourceid | transportid | networkid | frequency | inversion | symbolrate | fec  | polarity | modulation | bandwidth | lp_code_rate | transmission_mode | guard_interval | visible | constellation | hierarchy | hp_code_rate | mod_sys   | rolloff | sistandard | serviceversion | updatetimestamp     | default_authority |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
|       6 |        8 |          10 |       100 | 530000000 | a         |          0 | auto | v        | qam_64     | 8         | 2/3          | 8                 | 1/16           |       0 | qam_64        | n         | 2/3          | UNDEFINED | 0.35    | dvb        |             33 | 2011-01-15 17:26:10 |                   |
|       5 |        8 |          33 |       100 | 522000000 | a         |          0 | auto | v        | qam_64     | 8         | 2/3          | 8                 | 1/16           |       0 | qam_64        | n         | 2/3          | UNDEFINED | 0.35    | dvb        |             33 | 2011-01-15 17:26:10 |                   |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
2 rows in set (0.00 sec)

---

### Post by alien878 on 2011-01-18
If I understand you correctly, you have scanned channels, can watch them in liveTV, but have no schedule information.

First off, if you have done any manual changes to the sql channels data, I would recommend you delete all channels/cards and start again in the mythtv-setup.  I've found that some of the data in sql isn't what it seems when it comes to mythtv.

Then, make sure EIT is enabled on the capture card *and* the video source in mythtv-settings.

Next, go to mythweb settings -> channelinfo and make sure use on-air guide is checked for the channels (it might be possible to do this in mythtv-setup, but I've never tried it).

Wait a while without watching or recording TV.  If you still don't get EIT data, check the backend.log.  If there isn't anything obvious in there, start the backend with --verbose important,general,eit.  Then you should see something in the backend log.

Note that the first time though may take a long time for EIT to fully populate.  It depends a lot on how many channels you have.  If you are seeing EIT activity in the backend log, then I would give it a few hours to fully complete.  Despite what I would have thought, watching a channel doesn't cause the EIT to be immediately read for that channel (in my experience).

---

