---
title: "What have I done to Kaffeine?!"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by Giggity on 2007-07-27
I was having an issue playing a recently encoded XviD video (playback was jerky ~10fps), so somebody told me I should try changing the output driver under Kaffeine's "xine Engine Parameters" until I found a driver that played smoothly.  I selected a new driver, stupidly without knowing what it would do, and Kaffeine crashed.

Now anytime I try to play a video under Kaffeine, it crashes before starting the video.  I cannot change the output driver back to "default", because as soon as I select "xine Engine Parameters", Kaffeine crashes before the configuration window appears, saying something about a "Signal 11 error."

What can I do?!  I love Kaffeine!  It's not urgent as the other players still work well enough, but I'd like to know how to fix this if you can help.

---

### Post by hedgefighter on 2007-07-27
Try editing the config file: ~/.kde/share/apps/kaffeine/xine-config

FInd the lines that look like this:

```
# Videodriver to use (default: auto)
# { auto  dxr3  aadxr3  xv  SyncFB  opengl  xshm  none  xxmc  sdl  fb  xvmc }, default: 0
video.driver:[driver you chose]
```

And change the last line to this:

```
#video.driver:auto
```

---

### Post by Giggity on 2007-07-27
That worked.  Thanks for sharing your configuration expertise!

---

### Post by hedgefighter on 2007-07-27
No problem at all. Glad it helped.

---

### Post by ffoletti on 2007-07-30
Same problem, same solution...!
...how I love this forum....
thanks!

---

### Post by eldersoares on 2007-07-31
similar problem, wrong solution!
my kaffeine doesnt even open. i tried to open it through the terminal and nothing happens, noone message. if i try locale, nothing happens either...! what can i do??
thanks
(kubuntu edgy dell inspiron intel centrino duo 1.6ghz)

---

### Post by hedgefighter on 2007-07-31
Did you change the video driver too?

---

### Post by eldersoares on 2007-07-31
SOLVED!
the video driver was already as it should be.. i purged and installed again and nothing happened. so i searched a bit more in the forums and the solution was......
"killall kaffeine"

so i wonder why???? why such a simple solution for such a big problem??? what happens with apps in linux???? some simple actions can make things to stop completely!!!! i really dont understand... im a linux enthusiastic, i tell people to use linux, i tell people the advantages of using linux but, actually, errors like these never happened to me in win...

is there a problem of compatibilkity between all the different programs and developers in the world?????? in theory, things should work better w/ free software cause i think the community is much bigger than the number of workers in prop software companies...

maybe the solution is a kind of standardization or rules to develop in linux... dont know... i t makes me sad :(
thanksss!

---

### Post by hedgefighter on 2007-07-31
It seem like what happens was that kaffeine was already running and not presenting itself correctly or had not terminated correctly. When you tried to run it, it ignored your request because it was already running. So, by killing the process you allowed it to reopen.

The other option would be to hit Ctrl+Esc which opens your process table. That gives you the ability to kill processes with a GUI.

The fact of the matter is that the software's not perfect, no one claims it is. It's sadly the nature of software. I was running a thousand dollar program in windows the other day and it crashed for no reason. WIth PCs there's a huge ecosystem of software and hardware trying to work together. Apple has much more control, but I've many crashes in OS X too. I've run into tons of issues in Linux, though not as many as I had in Windows. Your experience will vary. But at least with Linux there's a fix out there and there are bug reporting facilities, and of course I have a hard time complaining about free software.

---

