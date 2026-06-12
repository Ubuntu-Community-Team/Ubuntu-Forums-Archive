---
title: "Guitarix: please how to connect JACK?"
date: 2015-11-12
forum: Multimedia Software
---

### Post by rva1945 on 2015-11-12
I know this is recurring, but after a while I reinstalled Ubuntu in a new PC, and want to use Guitarix. In JACK I have 

(readable clients)
gx_head_amp
   out_0
gx_head_fx
  out_0
  out_1
system
  capture_1
  capture_2

(writeable clients)
gx_head_amp
   in_0
gx_head_fx
  in_0
System
  (playbacks 1 to 6)

I tried some combinations, from no sound at all to an unbearable high pitched sound. Shouldn't this be easier? Please give me a working example before restarting the PC in W7.

---

### Post by rva1945 on 2015-11-12
I just had to reason it for a while: System captures into gx_heads_input, gh_head_amp outputs into systrem playbacks. Now I want to play an Mp3 while using Guitarix but that is a different story. Now, can I save the configuration or do I have to connect everything everytime?

---

