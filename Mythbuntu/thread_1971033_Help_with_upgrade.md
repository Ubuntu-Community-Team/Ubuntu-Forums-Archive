---
title: "Help with upgrade"
date: 2012-05-02
forum: Mythbuntu
---

### Post by lamogo on 2012-05-02
Hello,

I am usually never here since I can find the information and correct any problems myself but this one has me beat. I am an Linux only user and have been using Mythbuntu since 10.10. It worked great right-out-of-the-box but since I have not been able to upgrade in any manner. I was hoping that 12.04 would work just like 10.10 did but like the other times it doesn't.

There is a problem with the capture card I think. Live TV doesn't work. On previous failed upgrades it would mention about buffer failing too many times, this time it says please wait then goes back to the main screen.

My card is a winfast DV2000 and works fine in 10.10 and also works fine with VLC and TV Time now. In Myth if I scan channels it finds none, although I can see it with VLC. Again I have been having this particular issue since 11.04. No matter how I upgrade, either by disk, by Internet, or simply ONLY upgrading mythtv.


I had to bother you all but I am stumped and I love Linux and Mythtv and hope we can resolve this manner.

NOTE: I am using a analog tuner with an analog signal. I am also living in the Philippines.

---

### Post by lamogo on 2012-05-02
No help on this one?

---

### Post by nickrout on 2012-05-02
> **lamogo said:**
> No help on this one?

Not with the limited information you have given.

---

### Post by lamogo on 2012-05-02
oh, I'm sorry. What more information do you need?

---

### Post by Bucky Ball on 2012-05-02
> **nickrout said:**
> Not with the limited information you have given.

? Please request the information you need to help the OP, if you think you can. ;)

---

### Post by lamogo on 2012-05-02
I'm pretty familiar with Ubuntu since I've used it every day for two years now, but I've never had a problem I couldn't fix by searching the forums. I've never needed to look at the logs but I tried to figure it out today. I used the log grabber and the link is [http://pastebin.com/hw3ZJ9Xs](http://pastebin.com/hw3ZJ9Xs).

I cut out the stuff I thought was not needed since it pasted everything of the log. It began logging today (the 3rd) at 9:14, and I tried watching Live TV at 9:20.

Yesterday I tried completing setup but when I scanned for channels it didn't find any. I manually added a known good channel, channel 2. I think the log says it didn't find any channels but mythtv has one channel I manually added. I know Linux has detected the card right, since I can view and change channels with TV Time.

I really don't know what else I can tell you. I've had this particular problem for some time and always resulted to installing an older version I think Mythbuntu 10.04. But I'd like to fix it for good this time. Thanks for any help. I enjoy MythTV and would like to get this working.

---

### Post by nickrout on 2012-05-02
> **lamogo said:**
> I'm pretty familiar with Ubuntu since I've used it every day for two years now, but I've never had a problem I couldn't fix by searching the forums. I've never needed to look at the logs but I tried to figure it out today. I used the log grabber and the link is [http://pastebin.com/hw3ZJ9Xs](http://pastebin.com/hw3ZJ9Xs).

I cut out the stuff I thought was not needed since it pasted everything of the log. It began logging today (the 3rd) at 9:14, and I tried watching Live TV at 9:20.

Yesterday I tried completing setup but when I scanned for channels it didn't find any. I manually added a known good channel, channel 2. I think the log says it didn't find any channels but mythtv has one channel I manually added. I know Linux has detected the card right, since I can view and change channels with TV Time.

I really don't know what else I can tell you. I've had this particular problem for some time and always resulted to installing an older version I think Mythbuntu 10.04. But I'd like to fix it for good this time. Thanks for any help. I enjoy MythTV and would like to get this working.

Why do you need to scan for channels again? If you have a known working setup and upgrade to a new version, the channel setup should still be there.

---

### Post by azmyth on 2012-05-03
How did you install mythtv (which repo) and which rev of 0.25 do you have. I use an analog tuner card to and the original release had a nasty bug that wouldn't let analog tuner cards work properly. I guess many people no longer uses these card. :confused:

You'll probably need weekly builds of 0.25 to fix your prob.

---

### Post by lamogo on 2012-05-03
Well the need to scan for channels is irrelevant, the point is there seems to be a problem with MythTV and the tuner of the card.

I've upgraded by downloading Mythbuntu from a torrent, burning a disk, and installing on a formated hard drive.

One previous attempt I did read in a bug report that a person was having a similar problem and he added the weekly build and the problem went away, I was so excited I tried it and upgraded to .24 (I think) with the weekly build and still no dice. Disappointed I reverted back and left it alone 

I had mentioned before that I tried even just upgrading MythTV before and it had the same problems. My main reason for upgrading Linux is now it is 12.04 LTS and I won't be upgrading until the next LTS. The reason for upgrading MythTV, is the new features and to be able to watch the awesome system that it is develop and grow. As I understand, I am able to contribute to this growth, even though I don't program, by other means. One such way is reporting problems and trying to help find solutions, which is my intention here. My next step if it can't be resolved here is to file a bug, which I really do not want to do. I have kept a tight lip until now for the simple fact that I hate having to post to forums because most posters get nasty replies about their problems. They get told that the issue has been resolved at some post somewhere else and they need to research more. I am here as a last ditch effort before I make a decision to move to XBMC or the like.

---

### Post by nickrout on 2012-05-03
As the previous poster said, go to the very latest 0.25-fixes and see how that works.

There have been a number of problems with analogue, with livetv and a few other areas.

---

### Post by lamogo on 2012-05-03
ok thanks Nick. I added that repo via MCC and did and upgrade. It was d/Ling the files when I had left for work. It had around 100Mbs of data so it may be done by the time I get home. (Connections here are sub sub-par.) I'll let you know how it turns out and thanks for the help thus far.

---

### Post by lamogo on 2012-05-03
Sorry to report, but I came home and have seen that everything was upgraded correctly, mythTV is working but still having the same issue with the Tuner. You can view a new log here: [http://pastebin.com/1a3dDjxG](http://pastebin.com/1a3dDjxG). Around item 2745 is the important part but it says the same thing as before.

Is it time to report a bug?

---

