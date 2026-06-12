---
title: "mythfrontend crashes when exciting livetv"
date: 2009-06-28
forum: Mythbuntu
---

### Post by Eldis on 2009-06-28
I have a new problem with mythfrontend. When I exit livetv watching or watching a recording mythfrontend will segfault:
```
[ 2733.267866] mythfrontend.re[9851]: segfault at 0 ip 00007fb0da743697 sp 00007fb0dddab070 error 6
[ 2941.771133] mythfrontend.re[9923]: segfault at 0 ip 00007f5e3bdf6697 sp 00007f5e3f4f6090 error 6
[ 3805.423275] mythfrontend.re[10195] general protection ip:7f381ce87689 sp:7f381ffff078 error:0
[ 3834.051745] mythfrontend.re[10630] general protection ip:7f82cd2a067b sp:7f82d4a3c070 error:0
[ 4067.586932] mythfrontend.re[10686] trap invalid opcode ip:7f9702dd867a sp:7f97065d8078 error:0
[ 4108.612557] mythfrontend.re[10741] general protection ip:7f691920867a sp:7f6928962078 error:0
[ 4260.475538] mythfrontend.re[10980]: segfault at 7b055989 ip 00007f92b106267f sp 00007f92b4862078 error 6
[ 4672.816233] mythfrontend.re[11039]: segfault at 0 ip 00007f037f3b467a sp 00007f03829dc078 error 4
[ 7120.554679] mythfrontend.re[12028]: segfault at 72e452b0 ip 00007f215989467f sp 00007f215d014078 error 6
[ 7135.367006] mythfrontend.re[12212]: segfault at 7f122a3fc610 ip 00007f122a3fc610 sp 00007f122b83a078 error 14
```

Frontend log just before crash:
```
TV: Attempting to change from WatchingLiveTV to None
```

Any tips, could there be something wrong with my settings or hardware or maybe a bug in the latest myth version ?


 This is a backend + frontend combo running mythbuntu 9.04 64 bit

---

### Post by roundhay on 2009-06-28
try this, worked for me

[http://ubuntuforums.org/showthread.php?t=1145048](http://ubuntuforums.org/showthread.php?t=1145048)

---

### Post by Eldis on 2009-06-29
> **roundhay said:**
> try this, worked for me

[http://ubuntuforums.org/showthread.php?t=1145048](http://ubuntuforums.org/showthread.php?t=1145048)

Yeah worked for me aswell, thanks :)

---

