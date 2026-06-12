---
title: "HDhomerun Prime channel scan woes with 0.27 mythtv"
date: 2014-02-08
forum: Multimedia Software
---

### Post by ozooha on 2014-02-08
Hi Everyone,
I followed the setup as per the official page on [http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime](http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime)
to set up my network tuner. However I used a free xmltv grabber and so set the video source section to "no grabber".
I went ahead and did the channel scan in the input connection section using the cable and qam256 as my input choices.
Below is a snapshot of my channel table from the mythconverge database.

MariaDB [mythconverg]> select callsign,channum,xmltvid,name,serviceid,tvformat from mythconverg.channel;
+----------+----------+---------+-------------------------+-----------+----------+
| callsign | channum  | xmltvid | name                    | serviceid | tvformat |
+----------+----------+---------+-------------------------+-----------+----------+
| KIDS     | 13_2     |         | KIDS                    |       131 | ATSC     |
| V-ME     | 13_3     |         | V-ME                    |       199 | ATSC     |
| WCBS-HD  | 2_1      |         | WCBS-HD                 |       702 | ATSC     |
| WNET-HD  | 13_1     |         | WNET-HD                 |       713 | ATSC     |
| COZI-TV  | 4_2      |         | COZI-TV                 |       109 | ATSC     |
| WNBC     | 4_1      |         | WNBC                    |       704 | ATSC     |
| WNYW     | 5_1      |         | WNYW                    |       705 | ATSC     |
| WTBY-D1  | 54_1     |         | TBN                     |       134 | ATSC     |
| ION      | 31_1     |         | WPXN ION                |       703 | ATSC     |
| WNJU-HD  | 47_1     |         | WNJU-HD                 |       714 | ATSC     |
| WRNN-D1  | 48_1     |         | WRNN-D1                 |       762 | ATSC     |
| WMBC DT  | 63_1     |         | WMBC Digital Television |       763 | ATSC     |
| ThisTV   | 11_3     |         | ThisTV                  |       111 | ATSC     |
| Antenna  | 11_2     |         | Antenna                 |       114 | ATSC     |
| WWOR-TV  | 9_1      |         | WWOR-TV My9 Secaucus    |       709 | ATSC     |
| PIX11    | 11_1     |         | PIX11                   |       711 | ATSC     |


This however did not let me watch any live tv nor record for that matter.
I had a similar setup done with mythtv 0.26 (and later upgraded to 0.27) and below is a snapshot of the 
channel table in mythconverge.
mysql> select callsign,channum,xmltvid,name,serviceid,tvformat from mythconverg.channel;
+----------+---------+------------------------------+-------------+-----------+----------+
| callsign | channum | xmltvid                      | name        | serviceid | tvformat |
+----------+---------+------------------------------+-------------+-----------+----------+
| 702WC    | 702     | I702.28459048.microsoft.com  | 702 WCBSDT  |         0 | Default  |
| 703WP    | 703     | I703.195990477.microsoft.com | 703 WPXNDT  |         0 | Default  |
| 704WN    | 704     | I704.28459780.microsoft.com  | 704 WNBCDT  |         0 | Default  |
| 705WN    | 705     | I705.28457893.microsoft.com  | 705 WNYWDT  |         0 | Default  |
| 707WA    | 707     | I707.28455323.microsoft.com  | 707 WABCDT  |         0 | Default  |
| 709WW    | 709     | I709.43584439.microsoft.com  | 709 WWORDT  |         0 | Default  |
| 711WP    | 711     | I711.40553490.microsoft.com  | 711 WPIXDT  |         0 | Default  |
| 712N1    | 712     | I712.226556368.microsoft.com | 712 N12WCHD |         0 | Default  |
| 713WN    | 713     | I713.28456564.microsoft.com  | 713 WNETDT  |         0 | Default  |

You will notice that callsigns and channum between the tables are different. 
In fact the second table reflects the exact channel number as I see on the hdhomerun_config_gui
I later did a mysql dump of this (second) table into the former table (the first one) and LIVE TV worked!!!!
So what went wrong with the scan in 0.27 in the first table above?
IS there a defect in how the scan is being conducted for a HDHOMErun prime or am I doing some things wrong with my mythtv-setup.
Any insights into this is really appreciated.
OZooHA

---

