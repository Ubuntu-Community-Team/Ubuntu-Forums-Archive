---
title: "frontend bug on program change"
date: 2008-02-11
forum: Mythbuntu
---

### Post by david.birch on 2008-02-11
Hi,
  i'm having a very annoying problem of myth frontend stopping (not crashed, as i can escape to the menu & then click to resume live tv no probs) whenever (like 100% of the time) the program changes (on the same channel) - i have myth 0.20.2 ubuntu 01 installed on 7.10 std desktop, with hauppauge nova-t-500 & conexant cx88 tuners (issue exists when tuners tested in isolation), and i'm watching dvb-t streams in Sydney Australia.
I didn't get this problem with 0.20.1 compiled on gentoo, is anyone else getting this issue?

I initially thought the issue was with EIT & disabled that (i remember old drivers for the hauppauge caused issues), but that was a no go, i have found 2 messages in the logs:

either "LiveTV forcing JumpTo 1"
or "NVP: Prebuffer wait timed out 10 times"

i could see some older posts similar but with no resolutions..

any ideas ?

thanks
david

---

### Post by david.birch on 2008-02-12
sorry, i take back what i said about the EIT issue - i had only set the EIT switches to off on the videosources (by SQL then backend restart). After setting useonairguide to false in the channel table to i am no longer getting this issue. It seems to only appear on the hauppauge tuner though.

Not sure but i gather it is a driver issue :(

---

