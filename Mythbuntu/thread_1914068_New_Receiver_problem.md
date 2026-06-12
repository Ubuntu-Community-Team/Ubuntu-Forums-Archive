---
title: "New Receiver problem"
date: 2012-01-23
forum: Mythbuntu
---

### Post by Nobodyspeshul on 2012-01-23
I just swapped out my old receiver (yamaha) with a [Sony ]("http://www.amazon.com/Sony-STRDH720-Channel-Receiver-Black/dp/B004QOA92A/ref=sr_1_1?ie=UTF8&qid=1327352513&sr=8-1")

But now my sound isn't working.  The video is working fine, I'm using onboard HDMI to transmit my sound and video to my receiver.

Would this be a setting change on the receiver since it's the only component that has changed, or is it a new setting on myth that I need to change?

Still a bit of a novice with this, thanks guys.

---

### Post by nickrout on 2012-01-23
> **Nobodyspeshul said:**
> I just swapped out my old receiver (yamaha) with a [Sony ]("http://www.amazon.com/Sony-STRDH720-Channel-Receiver-Black/dp/B004QOA92A/ref=sr_1_1?ie=UTF8&qid=1327352513&sr=8-1")

But now my sound isn't working.  The video is working fine, I'm using onboard HDMI to transmit my sound and video to my receiver.

Would this be a setting change on the receiver since it's the only component that has changed, or is it a new setting on myth that I need to change?

Still a bit of a novice with this, thanks guys.

I would have a look at you/var/log/Xorg.0.log file and see what it says about the HDMI connection. My bet is that the Sony os not giving correct information about it's capabilities and your HDMI card responds accordingly.

---

### Post by Nobodyspeshul on 2012-01-24
I did a grep against the file and nothing came back for HDMI.

Is there a better way to look through the file to see how it may be affecting the input of the receiver?

---

### Post by gordintoronto on 2012-01-24
Did the old receiver also use HDMI? If not, you probably need to change Sounds Preferences to select HDMI output.

---

### Post by Nobodyspeshul on 2012-01-24
Yes it did and without problems, the settings internally on myth were alsa:hdmi and everything worked flawlessly.

---

### Post by kcaj on 2012-01-26
I see that the receiver has assignable inputs. Make sure that the receiver is expecting to receive audio through the HDMI input and not S/PDIF or analog input.

---

### Post by Nobodyspeshul on 2012-02-10
Just wanted to post a resolution.

I sat down last night and hammered away at it and it turns out the video drivers that I had changed to had disabled the sound output.

I swapped back to the original set of NVidia drivers and everything works great again!

Thanks everyone for the suggestions, you guys rule.

---

