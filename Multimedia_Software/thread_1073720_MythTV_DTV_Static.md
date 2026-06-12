---
title: "MythTV DTV Static"
date: 2009-02-18
forum: Multimedia Software
---

### Post by mastermindg on 2009-02-18
So I've finally got my TV tuner to work with Ubuntu.

I'm on Hardy, got a K-World ATSC 115 configured and all setup. It's working fine in Kaffeine after I used atsc-converter to convert my channels.conf to channels.dvb. The picture and sound are perfect in Kaffeine so I know the following:

1) MY TUNER IS WORKING !! :-)
2) MY TUNER IS ABLE TO TUNE ATSC !!

My problem is that it seems that MythTV is not properly setting the frequencies for broadcast ATSC. From the picture it looks like it's trying to pickup analog signals. I've set the grabber to local broadcast and removed analog stations from the list. However, when I pull up the channels they are not properly coded (i.e. 7.1, 7.2, etc). 

How can I fix it so that MythTV properly recognizes the ATSC stations and tunes accordingly?

---

### Post by mastermindg on 2009-02-18
Sorry about my stupidity.

I had my capture card set to analog. Had to set it to DVB.

Thanks. :popcorn:

---

