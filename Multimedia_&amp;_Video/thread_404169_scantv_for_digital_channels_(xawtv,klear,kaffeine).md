---
title: "scantv for digital channels (xawtv,klear,kaffeine)"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by angelman99 on 2007-04-08
I am trying to generate a channels list for my digital channels for the klear tv  or kaffeine or xawtv program.

```
scantv -C /dev/vbi -o /home/me/.klear/channels.conf
```

Which gets me

```
[global]
freqtab = australia

[defaults]
input = Television
norm = PAL

[unknown (7)]
channel = 7

[unknown (31)]
channel = 31

[unknown (34)]
channel = 34

[unknown (52)]
channel = 52

[unknown (55)]
channel = 55

[unknown (58)]
channel = 58

[unknown (61)]
channel = 61

[unknown (64)]
channel = 64
```

Call me a bit stupid but they are the analogue channels :confused: 
How do I get a suitable listing for klear or kaffeine or xawtv to use?

I have hand crafted a au-Rockhampton file for kaffeine and placed it in
/home/me/.kde/share/apps/kaffeine/dvb-t/au-Rockhampton

```
# Australia / Rockhampton (NTL Site MT HOPEFUL)
# aufreq=((UHF channel number)*8+306)

# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy

# ABC Digital TV
T 219500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
# ABC2 Digital TV
T 196240000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
# Seven Network
T 182260000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
# WIN Digital
T 226500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
# Southern Cross Ten
T 569250000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
# TNQ
T 585500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
# SBS
T 592500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
```

Which got SBS only into the channel list, all the information I can find online only tells you the basic information (channel and frequency, all the other stuff I've made educated guesses based on au-Brisbane and au-Mackay). Kaffeine goes through the motions of scanning and the little bars move up and down and the lock light flashes quite a bit but no new channels appear?

---

### Post by angelman99 on 2007-04-12
Wasted 5 days on this, reinstalled my Windows XP license, downloaded Media Portal (Freeware) had it up and running with my Compro Videomate DVB-T300 in 20 minutes (not including the Windows install and updates which was somewhere around the 2-3 hour mark - I have low speed ADSL). Hit the scan button and all my digital TV and Radio stations appeared.

I am still surprised that the Compro Videomate DVB-T300 can win over 26 awards and be so ignored and difficult to configure in ANY linux flavour. I know even here in Regional Australia that hundreds of these cards are being sold out here as it has all the features that most users are looking for in a budget priced card. And just quietly I am extremely happy with the quality of the picture on this card (both on a 17" CRT and on my NEC dataprojector).

I'll check back in with ubuntu in another six months. Awesome project keep up the brillant work, ubuntu is definitely my favourite linux distro.

---

