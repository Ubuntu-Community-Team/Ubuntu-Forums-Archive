---
title: "ATI graphics still choppy after installing driver."
date: 2006-02-14
forum: Multimedia &amp; Video
---

### Post by shade11 on 2006-02-14
Molmker told me that I should start a new thread  for this question to get the answer instead of asking in the driver discussion.

Well I finally got it installed properly. But now there is an issue I have.

- On some games and screensavers the graphics turn out slow and choppy. I know that my graphics card can take it but it isnt working. What do I do?


Please respond. . . If there is any info I need to post then please tell me.

Here is fglrxinfo:
```
ian@Jevelexwen:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5642 (8.22.5)

ian@Jevelexwen:~$
```

Here is an example:
I tried playing shogo MAD (Native linux port) on my lappy but it is too choppy and I have to stick with cruddy software acceleration. I played Shogo's Windows port on the same lappt]y and it runs super fast. Not to mention the fact that my praphics cars is 64Mb and I played shogo on a 32 Mb card and it ran perfectly. What is going on?

---

### Post by Zeroedout on 2006-02-15
How much ram do you have in your machine? Is your sound card funtioning optimally? What I'de do is boot into a low memory window manager like flwm and make sure that sound is disabled, and see how your framerate is. It will not be as good on windows becuase ATI's linux driver is shitty by comparison, however, it should be better than your described it.

---

### Post by shade11 on 2006-02-15
I have about 512 Ram and my sound card works normally. I will try that Window manager thing.

---

### Post by shade11 on 2006-02-16
Is there any sort of tweak (Even if dangerous.) or restricted package to make it work right?

---

