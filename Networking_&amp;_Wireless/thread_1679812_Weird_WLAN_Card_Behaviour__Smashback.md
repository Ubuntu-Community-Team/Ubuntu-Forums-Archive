---
title: "Weird WLAN Card Behaviour : Smashback"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by AngelDE98 on 2011-02-01
So , Hi ... again ... 

I had problems with my WLAN Card Firmware and DMA but these problems are fixed . Now , since yesterday , I need to shut my WLAN Card down at every ... I say , around 10th minute ( Time not static ) . And if I do ```
dmesg | wlan
``` ( my WLAN is wlan0 ) , I get ( just at the end ) ```
[28806.880068] [UFW AUDIT] IN= OUT=wlan0 SRC=192.168.2.102 DST=188.193.185.88 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=2275 DF PROTO=TCP SPT=41439 DPT=15223 WINDOW=5840 RES=0x00 SYN URGP=0 
[28809.144773] wlan0: direct probe to 00:23:08:ba:ba:4b (try 1)
[28809.344058] wlan0: direct probe to 00:23:08:ba:ba:4b (try 2)
[28809.544072] wlan0: direct probe to 00:23:08:ba:ba:4b (try 3)
[28809.744159] wlan0: direct probe to 00:23:08:ba:ba:4b timed out
[28820.443325] wlan0: direct probe to 00:23:08:ba:ba:4b (try 1)
[28820.640122] wlan0: direct probe to 00:23:08:ba:ba:4b (try 2)
[28820.840085] wlan0: direct probe to 00:23:08:ba:ba:4b (try 3)
[28821.040114] wlan0: direct probe to 00:23:08:ba:ba:4b timed out
[28831.748542] wlan0: direct probe to 00:23:08:ba:ba:4b (try 1)
[28831.948058] wlan0: direct probe to 00:23:08:ba:ba:4b (try 2)
[28832.148051] wlan0: direct probe to 00:23:08:ba:ba:4b (try 3)
[28832.348055] wlan0: direct probe to 00:23:08:ba:ba:4b timed out
[28843.057453] wlan0: direct probe to 00:23:08:ba:ba:4b (try 1)
[28843.256034] wlan0: direct probe to 00:23:08:ba:ba:4b (try 2)
[28843.456027] wlan0: direct probe to 00:23:08:ba:ba:4b (try 3)
[28843.656026] wlan0: direct probe to 00:23:08:ba:ba:4b timed out
[28854.371026] wlan0: direct probe to 00:23:08:ba:ba:4b (try 1)
[28854.568042] wlan0: direct probe to 00:23:08:ba:ba:4b (try 2)
[28854.768045] wlan0: direct probe to 00:23:08:ba:ba:4b (try 3)
[28854.968067] wlan0: direct probe to 00:23:08:ba:ba:4b timed out

```
repeated over and over again . It is since yesterday , and NO , I AM NOT IN EGYPT ! :lolflag: But I am in Germany . 
Some weeks ago , I changed from UBUNTU ( gnome , gdm ) to KUBUNTU ( kde , kdm ) and do not had such problems , just problems with sound where I need to link PulseAudio and Phonon to ALSA ( PA and P still need SoundCard Settings ) and ALSA to my right sound card . But this is another story and not such important , I think it is even an Feature ( System Sounds over Speakers ( PA ) and anything other over Headphones ( P , A ) ) . 

BTT ( Back To Topic ) : Can someone help me with my Timeouts ? Is it the fault of my mac adress , ip adress or router because of setting " mac adress filtering " to on ? I added my Laptop on the list . 

And I noticed that it happens mostly while my screencaver is used ( I use xscreensaver and had never problems and did not changed the screensaver ) . 

And I said Smashback ... If something happens , it is not comming alone ... 

Everytime if I download something or use Skype or something , my laptop lags horribly . Why ? 



It would help me much if you answer to problem 1 ( timeout ) and 2 ( lag ) . 

Thanks for Help
AngelDE98

PS : If you want to know : I have an Broadcom43 with ucode5-series .fw-files ( hard to get ) .

Edit : Just uploading this tread is making my WLAN stop ...  :lolflag:

---

### Post by AngelDE98 on 2011-02-01
Okaaaayyy ... UFW is the Firewall and GUFW has been configured properly ... But is my Firewall blocking my WLAN ? This would be unlogical . And after loosing connection to internet , disabling UFW and then connecting , still no internet until I restart my wlan card ... 


So : What is blocking WLAN ? Virus ? Firewall ? And is UFW short for Ubuntu FireWall ?

---

### Post by AngelDE98 on 2011-02-02
Ok , I found it : My BitTorrent Manager , Transmission . 

Theory ( I do a lot of them so I can check if I think the right thing ) : 

Transmission has blocked ports on my Firewall . Transmission wants to ignore it , gets focus and timeouts my firewall . With it it stops my Internet Connection . 

Is it right what I think ? And which Ports do need to be open ?

---

### Post by AngelDE98 on 2011-02-07
Just got worse : Every big file ( over 200 MB ) being downloaded is being catched by my Firewall and timing my WLAN CONNECTION out . Any solution ?

---

