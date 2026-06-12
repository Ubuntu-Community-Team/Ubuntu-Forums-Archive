---
title: "Xine crash with mythvideo"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by Dubstar_04 on 2007-04-01
When watching a video in mythtv using xine everything works fine untill i press 'quit' (stop or back - mce remote) at which point xine closes and the myth video screen is displayed but with no cover art and no film description and everything is frozen.

The only option to recover fron this is to ctrl - alt - backspace to the login screen.

I'm using feisty with the latest mythtv from the repos.

Anyone else seeing this or have any ideas?? is this an xine problem? when i log back in i get a crash report for xine. however it doesn't always crash and if it does it doesn't always produce a crash report!!

Crazy!!

---

### Post by superm1 on 2007-04-01
From the sounds of it, xine is still running when you hit stop.  Can you remotely connect to this computer during this time period and check the running processes?

---

### Post by Dubstar_04 on 2007-04-02
Thanks for getting back to me. This pc is a stand alone computer in the lounge and not networked. the problem is not always and issue as xine does sometimes close fine and the display returns to the chosen film with all the information displayed. 

I read on the fedoramythology about myth losing focus on return from xine but this does not seem like the same issue. never the less i have selected that the mouse hove will select the window and it has made no difference.  

Any other suggestions??

---

### Post by superm1 on 2007-04-02
Well if you can't remotely connect to the box to check running processes - i've got a few things.

First off, what is the command that you are using to launch xine?  It can be found in the mythvideo settings.

Next, what are the relevent sections of your ~/.lircrc that launch xine related items?  Particularly, stop, play, pause buttons on your remote.

Lastly, what window manager are you using?  


As a short experiment, when this happens you can try to go punch the quit key for xine into the keyboard at this computer.  I Think its q, and see if mythtv gains focus again.

---

### Post by Dubstar_04 on 2007-04-02
I pretty much followed your guide so i am using either gnome or openbox? as a window manager depening on how i'm logged in. 

```
 xine -r 4:3 -f -I --no-splash %s
```

 is my xine launch command


and the remote function is set to command 'quit' on both the back button and the stop button.

I set up the licrc file when using edgy and it all worked fine. Maybe its a  newer version of xine and it doesn't like one of the commands??

I have attached my lircrc for you to see. I've modified it quite a lot for a consistency with mythtv and xine usage.

What do you think??

---

### Post by superm1 on 2007-04-02
Okay,
right after your "-f"
add

```
--auto-play=q
```
so the command becomes:
```

 xine -r 4:3 -f --auto-play=q -I --no-splash %s
```

---

### Post by Dubstar_04 on 2007-04-02
Same still. xine did crash a few times saying something about plugins but then it worked!!

Is there any way to make the internal player any better?? Maybe use a certain codec? I would much prefer to use that rather than xine.

Thanks for your help.

Dubstar

---

### Post by superm1 on 2007-04-02
Well so this resolved the quitting problem?  Eg after finishing your video, its back to mythvideo right?

With regard to xine codecs support, its hit and miss with most files.  (Hit most the time though).  Once you get a feel for what formats work best with it, just stick to those generally.  So if you were transcoding your dvs to wmv, probably not a good idea.  Just put them in xvid and you'll have better luck.

Internal player is supposed to improve for 0.21, but can't comment much on that.  I'm staying away from a lot of excitement about 0.21 so I don't let myself down when I find out the release is another year off.

---

### Post by Dubstar_04 on 2007-04-02
Sorry I think my last post was miss leading. Xine plays fine but still doesn't return to mythvideo when  i quit!!

Ive been trying various commands

```
  xine -pfhq --no-splash 
```

The command doesn't seem to make any difference!!

Some times it does return to the video info properly, but some times it just kind of freezes / locks.
It really weird!!

---

### Post by superm1 on 2007-04-03
Okay, i think you need to experiment launching directly from a command line.  Launch and make sure that xine is closing when you hit the stop button.

---

### Post by Dubstar_04 on 2007-04-03
It works fine with no myth running. Im gonna uninstall all the xine and lib stuff and then reinstall everything.

It a really strange problem.

---

### Post by Dubstar_04 on 2007-04-03
I just installed the latest feisty updates and the crash problem has gone!!  There were quite a few of xorg and x11 updates so this may well have solved it.

I will repost if the problem returns!!

Superm1,
how do i get bigger fonts in and openbox session?? as when i use mythtv on a gnome session the fonts are big. but when i use the open box session described in your guide i get smaller fonts!!

Thanks for your help I really appreciate it as this mythbox is for my parents!! I'm converting my windows mediaportal box into a mythbox now i have seen how stable this one is!!  Roll on mythtv 0.21!!

---

### Post by superm1 on 2007-04-03
> **Dubstar_04 said:**
> I just installed the latest feisty updates and the crash problem has gone!!  There were quite a few of xorg and x11 updates so this may well have solved it.

I will repost if the problem returns!!

Superm1,
how do i get bigger fonts in and openbox session?? as when i use mythtv on a gnome session the fonts are big. but when i use the open box session described in your guide i get smaller fonts!!

Thanks for your help I really appreciate it as this mythbox is for my parents!! I'm converting my windows mediaportal box into a mythbox now i have seen how stable this one is!!  Roll on mythtv 0.21!!
Glad things are resolved here!  As for bigger fonts, you most likely want to set the DPI higher on your x server.  Nvidia card or something else?

---

