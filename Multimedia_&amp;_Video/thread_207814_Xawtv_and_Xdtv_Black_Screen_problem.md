---
title: "Xawtv and Xdtv Black Screen problem"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by MonkeyBoy on 2006-07-02
I got hold of a BT878 tv capture card the other day and was pleased to discover that TVtime works perfectly with virtually no work.  As I want to be able to record as well, I have tried several apps incuding Xawtv and Xdtv.  The problem is that whenever I start either app the screen goes black but the TV sound plays.  There doesn't seem to be any way to get out of the black screen other than restarting the xserver so I haven't been able to see a terminal in order to check for problems.

I am using an ATI Radeon 9800 which I suppose may be relevant.

Any suggestions on how to make either app run properly would be very welcome.

---

### Post by gborzi on 2006-07-02
I have had similar problems with the nvidia drivers. After some searching, I have found the solution for xawtv. Use the -noxv and -nodga (the latter is only needed with the 8756 drivers) switchs. Hope this helps.

---

### Post by MonkeyBoy on 2006-07-04
Cheers for your suggestions.

They didn't work unfortunately but I did find that if I reload the xserver, with Xawtv running, it does work...sort of.  The video is grainy and the record function doesn't seem to work properly so I might forget xawtv for now and crack on with setting up mythtv or freevo.

---

### Post by Icarosaurus on 2006-10-08
I've got the same problem: black screen while running Xawtv and KdeTV.
I have to shut down the xserver for having it work again.
TVTime works great instead...

I've got an ATI Radeon 9600.
Suggestions welcome! :-)

---

### Post by maitrebart on 2008-07-19
1) Go to a virtual console (ctrl-alt-f1).
2) Go back to X (ctrl-alt-f7).
3) You might get noise in the audio: just change channel.

Still don't know why the screen goes black when xawtv starts. I guess it is related to either compiz or fglrx or both.

If anyone has any idea, let us know!

---

