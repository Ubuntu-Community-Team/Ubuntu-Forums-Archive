---
title: "bad quality in live tv"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by ali780 on 2007-07-27
Hi 
Please have a look at: 

mms://81.12.12.198/irib5

In my computer for this live TV use Mplayer, but the quality is very bad. 
I also have uses totem, but the quality is as bad as Mplayer.
I want to know there is ant alternative for live TV with a better quality?
I must say that if I use windows for this live TV the quality is very good.
Thank you

---

### Post by dannyboy79 on 2007-07-27
I am, not sure what type of quality you're looking for. When you stream stuff it all depends on your connection to the server, their upload capability, mplayer buffering settings etc etc. I actually vnc'd into my machine at home thru an ssh tunnel and checked it out and even thru VNC it didn't look that bad, it just was jumpy because it's thru an encrypted ssh tunnel over vnc so I didn't expect to be good. Here's what it looked like for me.
[[IMG]http://img509.imageshack.us/img509/3769/tvthruvnccf4.png[/IMG]](http://imageshack.us)
Shot at 2007-07-27
I hope your picture is way better and if it's not, than you have a config problem. My mplayer is the default from Ubuntu Feisty Repo's. I have a 5megabit (per ISP, it's more like 3.5megabit's) download connection, what's yours? Also, are you sure this is LiveTV? Have you tried VLC to play the file?

---

### Post by ali780 on 2007-07-27
I have tried to use vlc but I have just voice. My internet connection 1s 24 Mb/s. but the quality is horrible in my computer. I don't know how do I configure my mplayer.

---

### Post by dannyboy79 on 2007-07-27
I am not sure what the 1s is but if you have 24megabits per second then that's for sure not your problem. I seriously doubt you have that as your download speed. Most cable providers provide a 5megabites/1.5megabits connection and dsl is around 768/348.These are of course rough estimates, and if you meant kilobits well that's more reasonable and faster than dialup so it should be a problem. Dialup is around 3-5kilobits.

 mplayer doesn't need any config, that's what I said, It's just the normal mplayer from the repositories with no changes.

---

