---
title: "Can I customize lirc like this?"
date: 2010-09-30
forum: Mythbuntu
---

### Post by Quadari on 2010-09-30
I have a MCE USB remote (it's the third one from the left on this page:
[http://www.mythtv.org/wiki/MCE_Remote#Media_Center_Remotes](http://www.mythtv.org/wiki/MCE_Remote#Media_Center_Remotes) )

In general it works just fine.  However, I was hoping to tweak some of the buttons.  I've tried playing around with the ~/.lirc/mythtv file, but haven't had success in getting things to work how I want.   Here's what I would like to happen:

1)  When I'm watching a recording, and I hit "Stop" I would like myth to set a bookmark (specifically to clear any previously set bookmark and set a new one at this point), and then escape back out of the recording.  In other words, this is what happens when you're watching a video tape (remember those?) on a VCR.  When you hit stop it stops playing and exits, but then when you hit play again it starts back up at the point you left off.

2)  Currently, when watching a recording, the "Up" and "Down" keys are just duplicates of the "Channel Up" and "Channel Down" keys.  Both of them move forward or backwards by 10 minutes.  This seems redundant.  However it would be nice to have the "Up" and "Down" keys move forward by 5 seconds, and backwards by 30 seconds, respectively.  (Thus they would be the compliment of what the "Right" and "Left" keys do.)  Is there a way to set this up?

Thanks for the help.

---

### Post by LowSky on 2010-09-30
lirc isn't were you will want to edit these commands. You will want to edit them from MythTV directly. 
1)Utilities/Setup > Setup > TV Settings > Playback > Action on Playback Exit (page 2)

2)The d-pad or the left/rigth arrow keys are already set to do this the way you wish. The up and down are set that way for faster skipping. Just an FYI you can change the amount of skip from the TV settings as well.

---

