---
title: "Puzzled: DVB-T second tuner temporarily unavailable"
date: 2011-08-22
forum: Mythbuntu
---

### Post by ceejay on 2011-08-22
MythTV 0.24-fixes, Ubuntu 11.04. Hauppauge dual DVB-T tuner receiving Freeview in the UK. Have set up the tuners (adapter0 and adapter1) and have configured the backend to allow up to three recordings per tuner - these show up as Encoders 1 to 6.  

Over the last few weeks, since I've set all this up, I've actively used both tuners successfully, including making simultaneous recordings from channels I know to be in different multiplexes.

Tonight, however, we were watching one show that had been set to record, about 10 minutes behind real time. Then another show was due to start recording, on another multiplex - a warning popped up on the screen. Unfortunately I can't remember the details - I was taken by surprise and really didn't want to miss what was going to happen next! We carried on watching our show, and I checked afterwards that the second show was indeed being recorded.

So far so good ... but ... I then found myself in the position where mythTV seemed to refuse to let me watch anything other than what was being recorded (except another channel on the same multiplex). In other words, it wouldn't use the other tuner. I checked the backend status with MythWeb, and it reported that only one of the six encoders was in use.

It was only when the second recording finished, and the tuner was released, that normal service was resumed. As I write, I have live TV on one tuner and recording (on a different multiplex) on another tuner.

So what went wrong? How can I stop it happening again? User error or bug?

Any advice much appreciated - I just lost a few WAF points!

TIA
Ceejay

---

### Post by ceejay on 2011-08-23
Well, 24 hours later ... and something very similar has happened again, which makes me think this isn't user error. No on screen messages this time though. But as I write, the second recording (2200-2300) is running on Adapter1/Encoder 3 ... the other Adapter and its three virtual encoders are not in use, but I cannot "Watch TV" on any channel that isn't in the same multiplex as the current recording: if I try, I just get to see the channel that is being recorded.

Exiting and restarting the front end makes no difference.

However, I can go the the programme guide and set a recording rule for another channel, and it will record, and I can watch it while its recording. I know this is some kind of workaround, but it has a very low WAF!

Does anyone have any idea why I can set a recording going on a channel, but can't watch it as "Live TV"?

Ceejay

---

### Post by bance on 2011-08-24
I think this is expected behaviour, Mythtv defaults to the first tuner that is set up in the capture card section of mythtv set-up for viewing live tv.

It also defaults to record from the first tuner in the same set-up section, which is why one is encouraged to set up the best tuner first!

If your rig is set this way then you can only view channels on the same mux as is being recorded, unless you  use the menu (press 'm') and select another tuner (card not 'virtual' tuner).

However, there is a setting..... avoid conflicts with live TV....  Which if selected will make the default tuner for live TV the last tuner entered at the capture card screen in myth set-up, this should probably suit your needs, of course, if there is more than one recording being made, one would still be bound by the 'mux' limitation... assuming there are only two tuners.

I thought all this was in the 'FM' as in 'RTFM' but after a quick scan of docs and wiki, I couldn't find it.... Maybe I read it somewhere else!

HTH Steve.

---

### Post by ceejay on 2011-08-25
Steve

Many thanks for taking the trouble to reply.

I'm not entirely sure about your use of "expected", though! :-)
It does seem more than a little odd that "Live TV" is not capable of using any available tuner, when the scheduler can.

In any case, there is something else going on here.  As I write I now have 2 current recordings, on BBC2 and BBC4 (which are on different multiplexes, hence using both tuners). The backend status reports:
```

Encoder 1 [ DVB : /dev/dvb/adapter0/frontend0 ] is local on aristotle and is recording 'The Duchess' on BBC TWO. This recording is scheduled to end at 10:45 PM.
Encoder 2 [ DVB : /dev/dvb/adapter0/frontend0 ] is local on aristotle and is not recording.
Encoder 3 [ DVB : /dev/dvb/adapter1/frontend0 ] is local on aristotle and is recording 'The Killing' on BBC FOUR. This recording is scheduled to end at 11:00 PM.
Encoder 4 [ DVB : /dev/dvb/adapter1/frontend0 ] is local on aristotle and is not recording.
Encoder 5 [ DVB : /dev/dvb/adapter0/frontend0 ] is local on aristotle and is not recording.
Encoder 6 [ DVB : /dev/dvb/adapter1/frontend0 ] is local on aristotle and is not recording.

```

If your explanation were correct, I would expect to be able to use Live TV to watch any channel that shared a multiplex with either of the two current recordings - but I can't. It will let me watch BBC Parliament (whoopee!!) which is on the same mux as BBC Four, but not BBC One or Three, which share a mux with BBC Two.

I had noticed the "avoid conflicts with Live TV" but have to say I didn't really understand what this setting does (and, given what I'm observing, I'm not sure I do now either!)

I found this thread relevant, though I think I'm still in the realm of "workarounds" rather than having it quite as I want it.
[http://www.mythtv.org/pipermail/mythtv-users/2011-April/313318.html](http://www.mythtv.org/pipermail/mythtv-users/2011-April/313318.html)

From this I am inferring that there is a limitation in that LiveTV will only make use of the tuner that it sees as currently in use, and that I have to use one of a number of tricks to make it look at another one.

So I guess my question becomes, how can I best set this up to make the system have an acceptable WAF?

Thanks fo all inputs
Ceejay

---

### Post by bance on 2011-08-25
Ceejay,

I think the thread you pointed out is where I read the 'expected behaviour' element of my reply.... ie. myth is behaving in the manner to which it is designed.

I understand your frustration, it happens to me occasionally, although not often, thankfully. I have a system that has four tuners (five actually but I've yet to get the last one to work nicely).

If the changing [source or card] option isn't working for you, and you really do need to watch and record three programmes at once, probably the easiest solution would be to get another tuner. They can be purchased quite cheaply, and using a usb version helps if your mother-board is fully populated.

If you were really keen I suppose you might try to programme a button on your remote to select another card, so as to avoid going through the menu system.

I think there is an option somewhere, that only shows channels available to the particular tuner in question, although this won't solve the problem, it may improve the WAF factor.

I think if you want to watch a recording in progress, you need to go to >>media library>>watch recordings..

HTH Steve.

---

### Post by ceejay on 2011-08-26
In case anyone else is following this, there is more info here:
[http://www.gossamer-threads.com/lists/mythtv/users/489018?page=last](http://www.gossamer-threads.com/lists/mythtv/users/489018?page=last)

and, in great detail, here:
[http://www.gossamer-threads.com/lists/mythtv/dev/369358#369358](http://www.gossamer-threads.com/lists/mythtv/dev/369358#369358)

and, in hardly any detail, here:
[http://www.mythtv.org/wiki/Multirec#Setup_Tuners_.2F_Capture_Cards](http://www.mythtv.org/wiki/Multirec#Setup_Tuners_.2F_Capture_Cards)

A good illustration of the conflict between devs for whom MythTV is a PVR, and some users who want a TV program that also records. In this case it is clear that the logic as-designed is not optimal, but it's also pretty clear that to rewrite it to cover all the possibilities might be a big job. I don't fancy it, so who am I to complain?

Except perhaps about the lack of documentation!

Just one other comment: adding extra tuners is a possibility: there is a spare slot in the box, and it's not a lot of money. However there is an electrical downside to this - further splitting my aerial will reduce signal quality, and adding a local amplifier isn't a good idea as there is already one in the loft. To make this work I'm going to have to run another cable from loft to the backend location......

Ceejay

---

