---
title: "Update regression: no sound on youtubes"
date: 2017-03-10
forum: Multimedia Software
---

### Post by PaulBx on 2017-03-10
$ uname -a
Linux len780 4.4.0-66-generic #87-Ubuntu SMP Fri Mar 3 15:29:05 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Just refreshed my 16.04 LTS and now no youtube sound in the firefox browser. When I play a youtube there is a warning at the top of the screen, "To play audio you may need to install the required PulseAudio software", with a button that says "Learn how". When I push the button, I end up on a mozilla support page with a message, "page not found".

I have a few .wmv files on my computer and they play just fine.

When I try an older Seamonkey, that I still have installed, it plays youtube audios just fine.

I tried "dmesg" and got this:
```

[   95.389459] audit_printk_skb: 153 callbacks suppressed
[   95.389463] audit: type=1400 audit(1489172830.501:63): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/proc/4660/net/arp" pid=4667 comm=4C696E6B204D6F6E69746F72 requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   95.616935] audit: type=1400 audit(1489172830.730:64): apparmor="DENIED" operation="file_mprotect" profile="/usr/lib/firefox/firefox{,*[^s][^h]}//lsb_release" name="/usr/bin/python3.5" pid=4682 comm="lsb_release" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   97.141522] audit: type=1400 audit(1489172832.254:65): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/etc/xdg/lubuntu/applications/mimeinfo.cache" pid=4660 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   97.266873] audit: type=1400 audit(1489172832.378:66): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4703 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  101.527840] audit: type=1400 audit(1489172836.645:67): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4703 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  101.530236] audit: type=1400 audit(1489172836.649:68): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4703 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  104.583897] audit: type=1400 audit(1489172839.698:69): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/sys/devices/system/node/node0/meminfo" pid=4742 comm=57656220436F6E74656E74 requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  189.540231] audit: type=1400 audit(1489172924.971:70): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/sys/devices/system/node/node0/meminfo" pid=4660 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  398.466325] uvcvideo: Failed to query (GET_DEF) UVC control 13 on unit 1: -32 (exp. 8).
[  398.466819] uvcvideo: Failed to query (GET_DEF) UVC control 13 on unit 1: -32 (exp. 8).
[  398.467322] uvcvideo: Failed to query (GET_DEF) UVC control 13 on unit 1: -32 (exp. 8).
[  398.467777] uvcvideo: Failed to query (GET_DEF) UVC control 13 on unit 1: -32 (exp. 8).
[  398.468264] uvcvideo: Failed to query (GET_DEF) UVC control 13 on unit 1: -32 (exp. 8).
[  398.525154] traps: guvcview[5354] general protection ip:7febb87b1d44 sp:7fff32f69af0 error:0 in libpthread-2.23.so[7febb87a8000+18000]
[  430.234527] audit: type=1400 audit(1489173165.654:71): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/proc/5450/net/arp" pid=5457 comm=4C696E6B204D6F6E69746F72 requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  430.326327] audit: type=1400 audit(1489173165.746:72): apparmor="DENIED" operation="file_mprotect" profile="/usr/lib/firefox/firefox{,*[^s][^h]}//lsb_release" name="/usr/bin/python3.5" pid=5472 comm="lsb_release" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  431.673349] audit: type=1400 audit(1489173167.094:73): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/etc/xdg/lubuntu/applications/mimeinfo.cache" pid=5450 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  431.780029] audit: type=1400 audit(1489173167.202:74): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=5487 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  435.709768] audit: type=1400 audit(1489173171.130:75): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=5487 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  435.712535] audit: type=1400 audit(1489173171.134:76): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=5487 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[  438.401998] audit: type=1400 audit(1489173173.822:77): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/sys/devices/system/node/node0/meminfo" pid=5525 comm=57656220436F6E74656E74 requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  523.724089] audit: type=1400 audit(1489173259.145:78): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/sys/devices/system/node/node0/meminfo" pid=5450 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
paul@len780:~$ 


```

I thought I turned off apparmor checking of firefox because of earlier problems. Is each update going to turn it back on? I suppose I need to find out why apparmor is complaining about firefox.

---

### Post by kostkon on 2017-03-10
Latest version of Firefox requires PulseAudio for audio. It only affects Lubuntu because it is the only Ubuntu distro that does not use PulseAudio by default. You can follow the discussion [on this thread]("https://ubuntuforums.org/showthread.php?t=2355092") for more information and possible solutions.

---

### Post by PaulBx on 2017-03-10
Thanks so much for finding that!

Another gripe against Firefox. I'm getting ready to dump it these days.

---

