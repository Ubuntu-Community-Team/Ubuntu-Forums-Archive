---
title: "Program not found in PAT"
date: 2012-04-28
forum: Mythbuntu
---

### Post by NautiusMaximus on 2012-04-28
I had to retune everything earlier this month as a result of the big Freeview retune in the London area.

This seemed to work, and as far as I can tell things are now working normally. However, I'm seeing some error messages in my backend log and I'm not sure what to make of them. This is the output:

```
2012-04-28 10:25:58.818 Program #22080 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(53) extension(0x2005)
      version(2) current(1) section(0) last_section(0)
         tsid: 8197
 programCount: 11
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number  8261 has PID 0x 100   data  0x20 0x45 0xe1 0x 0
  program number  8325 has PID 0x 102   data  0x20 0x85 0xe1 0x 2
  program number  8643 has PID 0x 112   data  0x21 0xc3 0xe1 0x12
  program number  8384 has PID 0x 108   data  0x20 0xc0 0xe1 0x 8
  program number  8452 has PID 0x 10c   data  0x21 0x 4 0xe1 0x c
  program number  8448 has PID 0x 10b   data  0x21 0x 0 0xe1 0x b
  program number  8442 has PID 0x 10e   data  0x20 0xfa 0xe1 0x e
  program number  8577 has PID 0x 120   data  0x21 0x81 0xe1 0x20
  program number  8500 has PID 0x 121   data  0x21 0x34 0xe1 0x21
  program number  8361 has PID 0x 122   data  0x20 0xa9 0xe1 0x22

2012-04-28 10:25:59.292 ProcessPAT: Program not found in PAT. 
			Rescan your transports.
2012-04-28 10:25:59.295 Desired program #22080 not found in PAT.
			Can Not create single program PAT.
```

I did at one stage have a rogue unidentified channel in my channel list. I think (although I'm not absolutely sure) it had a channel number 22080, but it only had a number, no name, and it didn't seem to be broadcasting anything I could watch. So I deleted it. However, I'm still getting the output above.

Does this matter? And if so, any idea how I could fix it?

I'm not sure that rescanning my transports is likely to achieve anything, given that I have very recently completely rescanned everything and as far as I know there have been no changes to what's being broadcast round here since then.

Thanks
NM

---

### Post by NautiusMaximus on 2012-04-29
Oh, sorry, should also have mentioned that I'm using Mythbuntu 10.04

---

### Post by ian dobson on 2012-04-30
Hi,

Rerun a channel scan. The error means that MythTV can't find the reqested channel in the expected multiplex. It could well be that you TV provider changed a reference within the multiplex.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2012-05-05
Thanks Ian. Have rescanned my channels. It found a surprising number of changes, considering I did the last scan after the major rearrangement of the Freeview services. Odd that they should change things again so soon.

Anyway, will keep an eye on the logs to see if those error messages go away.

NM

---

### Post by NautiusMaximus on 2012-05-06
Hm. Well, this proved to be quite complicated, but I think I may have fixed it.

I did a channel scan, and the error messages went away. However, so did a number of my channels! Several channels, including Film 4 and ITV 4, which I noticed were all on the same mux, were obviously found to some extent as they appeared in the channel list, but were associated with no programme information and didn't show any kind of signal.

I checked the log, and had new error messages about "wrong PMT". A little bit of googling took me to this page, which described the same messages I had:

[http://code.mythtv.org/trac/ticket/9976](http://code.mythtv.org/trac/ticket/9976)

That had the helpful advice that it was necessary not only to delete all existing channels before rescanning, but also all existing transports. Previously, I'd only deleted the channels.

So, I've deleted all channels and transports and rescanned. I now seem to have all the channels I should have. Will keep an eye on the logs and see if there are any further error messages.

---

