---
title: "'The Sound of Silence' message in BBC Radio 3 iPlayer popup (firefox 31 in 12.04)"
date: 2014-08-06
forum: Multimedia Software
---

### Post by interglossa on 2014-08-06
I am still running 12.04 but having problems with iPlayer (I am in the US).  I now get the 'Sound of Silence' screen when I try running iPlayer from firefox or chromium browser.  I don't get it when listening via tunein.com on my smartphone so it is not the feed.  Is there a problem with the flash plugin or BBC's support of it?

My flash is stock from the repository 11.2.202.394.

I also find I can't change the bandwidth from high definition to standard definition through the interface on the web browser popup, which I thought might help.  I have seen this posted in the last few months in various flavors but I wasn't having problems until recently.

---

### Post by ajgreeny on 2014-08-06
your problem is simply that the BBC limits use of iPlayer to IP addresses in the UK only; use in the USA is blocked.

It is supposedly possible to use a proxy connection sited in the UK, but I can not help with that.

---

### Post by steeldriver on 2014-08-06
My experience has been that the *radio *channels are **not **restricted to UK IPs - however I am also getting the "Sound of Silence" page for Radio 3 currently.

---

### Post by interglossa on 2014-08-06
Right - we are getting an error page after it plays correctly for a while.  I keep thinking if I knew how to adjust the bandwidth down then it would work, but the interface is too cryptic for me to figure out how - if that is even possible.

---

### Post by steeldriver on 2014-08-06
Right, for me it seems to be a problem only with 'Listen Live' streams in HD audio format - regular quality live streams (e.g. Radio4) and recorded Radio3 programs are OK

The old in-browser i-player used to allow a choice of High or Low bandwidth streams, but that does not seem to be an option any more

---

### Post by ajgreeny on 2014-08-06
One alternative for you might be to listen to live broadcasts using the media-player file streams available from a list at [http://bbcstreams.com/m/index.html](http://bbcstreams.com/m/index.html)
For example [http://www.bbc.co.uk/radio/listen/live/r3.asx](http://www.bbc.co.uk/radio/listen/live/r3.asx).

I realise this is no good for post-broadcast, iPlayer listening, but for that I wonder if you have tried get_iplayer 2.86-2-g969bd34-ppa17 which is available from the [https://launchpad.net/~jon-hedgerows/+archive/ubuntu/get-iplayer](https://launchpad.net/~jon-hedgerows/+archive/ubuntu/get-iplayer) ppa.  I am pretty sure that will not work in USA for BBC TV, but perhaps it does for radio?

---

### Post by interglossa on 2014-08-07
ajgreeny, thanks so much for these links!  I am able to hear through the .asx links and totem.  I will experiment with get_iplayer when I have time.  Americans with a VPN service should be able to view BBC programs although I have not tried this.

---

### Post by shantiq on 2014-08-07
flash may not be the issue interglossa maybe **try the latest version of get-iplayer** as suggested by  ajgreeny and you can stream programs that way [not record** just **stream]   no problems outside UK   TV is not allowed outside borders due to licence fee     does not affect radio programs

```
get-iplayer --type radio
``` to see all the available programs for replay

more refined search    ```
[COLOR=#333333][FONT=Consolas]get_iplayer --type [/FONT][/COLOR][COLOR=#333333][FONT=Consolas]radio "stanshall"[/FONT][/COLOR]
```

then say you pick

Added: **13196**: Vivian Stanshall's Radio Flashes - Episode 1, BBC Radio 4 Extra, Entertainment,Radio



simply run

```
get_iplayer --stream --type=radio -g **13196** | mplayer -cache 128 -
```


**PS**

this here will play BBC radio 3 HD worldwide if you wish for that too    the first in wma   the second in m4a both 320k 
change cvlc to vlc or nvlc if you so desire.


```
cvlc  "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio3/radio3_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
``` 

**m4a**


```
[COLOR=#000000][FONT=Ubuntu Mono]cvlc [/FONT][/COLOR]"http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls"


```[corrected]

---

### Post by ajgreeny on 2014-08-07
> **shantiq said:**
> flash may not be the issue interglossa maybe **try the latest version of get-iplayer** as suggested by  ajgreeny and you can stream programs that way [not record** just **stream]   no problems outside UK   TV is not allowed outside borders due to licence fee     does not affect radio programs

```
get-iplayer --type radio
``` to see all the available programs for replay

more refined search    ```
[COLOR=#333333][FONT=Consolas]get_iplayer --type [/FONT][/COLOR][COLOR=#333333][FONT=Consolas]radio "stanshall"[/FONT][/COLOR]
```

then say you pick

Added: **13196**: Vivian Stanshall's Radio Flashes - Episode 1, BBC Radio 4 Extra, Entertainment,Radio



simply run

```
get_iplayer --stream --type=radio -g **13196** | mplayer -cache 128 -
```


**PS**

this here will play BBC radio 3 HD worldwide if you wish for that too    the first in wma   the second in m4a both 320k 
change cvlc to vlc or nvlc if you so desire.


```
cvlc  "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio3/radio3_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
``` 


```
cvlc  "http://bbcmedia.ic.llnwd.net/stream/bbcmedia_lc1_radio3_p?s=1406383888&e=1406398288&h=a77c76440d279038b9b8c699c18d2d7d"
```

Thanks for that; I was not aware of those two final possibilities.  However the first worked fine, but the second just threw errors on my machine.
```
[0x7f7620001568] access_http access error: error: HTTP/1.0 403 Forbidden
[0x7f7620001568] access_http access error: error: HTTP/1.0 403 Forbidden
[0x7f7620001568] access_mms access error: error: HTTP/1.0 403 Forbidden
[0x7f7630000b28] main input error: open of `http://bbcmedia.ic.llnwd.net/stream/bbcmedia_lc1_radio3_p?s=1406383888&e=1406398288&h=a77c76440d279038b9b8c699c18d2d7d' failed
[0x7f7630000b28] main input error: Your input can't be opened
[0x7f7630000b28] main input error: VLC is unable to open the MRL 'http://bbcmedia.ic.llnwd.net/stream/bbcmedia_lc1_radio3_p?s=1406383888&e=1406398288&h=a77c76440d279038b9b8c699c18d2d7d'. Check the log for details.
```Any thoughts?

---

### Post by shantiq on 2014-08-07
had a deeper look aj/interglossa :)    these should work globally
[B]

Other BBC Stations in wma and m4a
[/B]
[http://iplayerhelp.external.bbc.co.uk/help/playing_radio_progs/real_wma_streams](http://iplayerhelp.external.bbc.co.uk/help/playing_radio_progs/real_wma_streams)
[http://iplayerhelp.external.bbc.co.uk/help/playing_radio_progs/local_radio_streams](http://iplayerhelp.external.bbc.co.uk/help/playing_radio_progs/local_radio_streams)
also   [http://www.listenlive.eu/uk.html](http://www.listenlive.eu/uk.html)


radio1   ```
cvlc mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio1/radio1_bb_live_ep1_sl0?BBC-UID=a5b3bed34bddb39c0c8ef21b21ebbf8c337b73e4906032d1a2581054d4edc2e4&amp;SSO2-UID=
```

```
cvlc "http://www.bbc.co.uk/radio/listen/live/r1_aaclca.pls"

```

radio1 xtra 

```
cvlc http://www.bbc.co.uk/radio/listen/live/r1x_aaclca.pls

```

radio2   ```
cvlc  "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio2/radio2_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
```
```
cvlc "http://www.bbc.co.uk/radio/listen/live/r2_aaclca.pls"

``` 


radio3  ```
cvlc  "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio3/radio3_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
```
```
cvlc "http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls"

``` 


radio4  ```
cvlc  "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio4/radio4_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
```
```
cvlc "http://www.bbc.co.uk/radio/listen/live/r4_aaclca.pls"

``` 


radio4 xtra  ```
cvlc "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio4/radio4xtra_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
```
```
cvlc http://www.bbc.co.uk/radio/listen/live/r4x_aaclca.pls

```

radio5   ```
cvlc "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio5/radio5_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
```
```
cvlc http://www.bbc.co.uk/radio/listen/live/r5l_aaclca.pls

```

radio5 Sport  ```
cvlc "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio5/5spxtra_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
```
```
cvlc http://www.bbc.co.uk/radio/listen/live/r5lsp_aaclca.pls

```

radio6   ```
cvlc "mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/6music/6music_bb_live_ep1_sl0?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
```
```
cvlc "http://www.bbc.co.uk/radio/listen/live/r6_aaclca.pls"

```


World Service   ```
cvlc  "mms://a973.l3944038972.c39440.g.lm.akamaistream.net/D/973/39440/v0001/reflector:38972?BBC-UID=95c354c3dc14d363574cfc5d212c9b581bfde85cc424e1deaab1a434a8e4a2d0&amp;SSO2-UID="
```



[B]to record any of them:


[/B]```
cvlc --run-time=3600 "http://www.bbc.co.uk/radio/listen/live/r6_aaclca.pls"[COLOR=#a52a2a]   /[/COLOR]
 --sout "#duplicate{dst=std{access=file,mux=mp4,dst=/home/[COLOR=#b22222]yourname[/COLOR]/Desktop/[COLOR=#b22222]NAME_OF_FILE [/COLOR]["%a-%d-%b-%Y" Time "%H&#10039;%M&#10039;%S"].m4a}" vlc://quit ;
```


of course change station and duration of recording accordingly








[B]========================================
[/B]

This time of year you have the Proms [if any of you like Classical]

so

```
get-iplayer --type radio  "proms"
```

and to write to desktop [easier perusal]

```
**get-iplayer --type radio  "proms"  2>&1 | tee    ~/Desktop/proms.txt**


```

and then for example to stream


```
get-iplayer --stream --type=radio -g 10567 [COLOR=#000000][FONT=Ubuntu Mono]| mplayer -cache 128 -[/FONT][/COLOR]

```

---

### Post by interglossa on 2014-08-10
Thanks shantiq and ajgreeny - it is nice to know there is this world-wide crowd of BBC (and Proms!) fans...

---

