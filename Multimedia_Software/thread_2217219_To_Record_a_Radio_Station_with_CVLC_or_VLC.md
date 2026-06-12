---
title: "To Record a Radio Station with CVLC or VLC"
date: 2014-04-16
forum: Multimedia Software
---

### Post by shantiq on 2014-04-16
This is a follow up from a previous [thread]("http://ubuntuforums.org/showthread.php?t=1359656&page=3")

[B]Command Line
[/B]
RECORD RADIO


```
cvlc --run-time=3600 YOURRADIOURL --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/YOURNAME/Desktop/NAMEOFYOURFILE $(date +"%A %Y-%d-%m [%r]").mp3}" vlc://quit ;



```



example:

```
cvlc --run-time=3600 http://95.141.45.144:8036 --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/YOURNAME/Desktop/Purple Piper 03 $(date +"%A %Y-%d-%m [%r]").mp3}" vlc://quit ;
```

[/QUOTE]







If your station plays **in aac  wma or ogg**:


```
cvlc --run-time=30 http://46.20.3.204:80 --sout "#duplicate{dst=std{access=file,mux=mp4,dst=/home/YOURNAME/Desktop/Kral $(date +"%A %Y-%d-%m [%r]").m4a}" vlc://quit ;
```



```
cvlc --run-time=30 mms://streaming.intoscana.it/wmtencoder/rtc.wma --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/YOURNAME/Desktop/Toscana $(date +"%A %Y-%d-%m [%r]").wma}" vlc://quit ;

```


```
cvlc --run-time=30 http://music.myradio.ua:8000/Classica128.ogg --sout "#duplicate{dst=std{access=file,mux=ogg,dst=/home/YOURNAME/Desktop/Classica128 $(date +"%A %Y-%d-%m [%r]").ogg}" vlc://quit ;
```

---

### Post by shantiq on 2014-10-12
[B]To Record BBC Radio live anywhere in the world in wma




[/B]**Radio 1    **


wma

> cvlc --run-time=3600 "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio1/radio1_bb_live_ep1_sl0?BBC-UID=a5b3bed34bddb39c0c8ef21b21ebbf8c337b73e4906032d1a2581054d4edc2e4&amp;SSO2-UID=" --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/[COLOR=#b22222]yourname[/COLOR]/Desktop/[COLOR=#b22222]Name Of Your File[/COLOR] [COLOR=#b22222]$(date +"%A %Y-%d-%m [%r]")[/COLOR].wma}" vlc://quit ;






change duration of recording to suit


[B]Radio 2   replace address in earlier command
[/B]
 "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio2/radio2_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="






**Radio 3**

 "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio3/radio3_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID=" 




[B]Radio 4
[/B]

 "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio4/radio4_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="


[B]Radio 5
[/B]

"mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio5/radio5_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="



[B]Radio 6    
[/B]
"mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/6music/6music_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="



[http://www.computerhope.com/unix/udate.htm](http://www.computerhope.com/unix/udate.htm)   for time switches
[http://iplayerhelp.external.bbc.co.uk/help/playing_radio_progs/real_wma_streams](http://iplayerhelp.external.bbc.co.uk/help/playing_radio_progs/real_wma_streams)    for all streams [right-click on station to find url]

---

