---
title: "Tutorial: Installing an ATI TV Wonder 200 under Mythbuntu (or Feisty)"
date: 2007-10-12
forum: Mythbuntu
---

### Post by CaptainPatent on 2007-10-12
Firstly, I would like to say that if you are in the market for a card and want to find a decent one, the ATI TV Wonder 200 is NOT the way to go! The card itself needs to be heavily tweked under linux to look decent and there are other great card choices in the same price range. If you happen to have a TV Wonder 200 lying around and just want to see what this whole Mythbuntu thing is about, there are a few small additional things you will (probably) need to do to get your TV Wonder working.

Firstly, Install Ubuntu / MythTV as usual and go ahead and configure your backend and frontend. Note that the backend will complain because the driver is not yet properly recognized (i.e. It will say "generic driver" when selecting the card type, it will not detect any channels, and it will complain that it didn't find any channels - this is fine, just say "I know what I'm doing" and quit the backend after you're done configuring (we will come back to the backend in a bit to finalize everything).

Now keep in mind the driver which can run this card is installed by default but for some reason the card is not recognized. We're going to create the file to define our card.

Navigate to the /etc/modprobe.d/ directory and create a file named cx88xx containing the text: options cx88xx card=4 tuner=44

This is most easily accomplished by:

```
cd /etc/modprobe.d/
sudo su -c 'echo "options cx88xx card=4 tuner=44" > cx88xx'
```

We then need to reload the module which can be accomplished by:
```
sudo modprobe -r cx8800
sudo modprobe cx8800
```

You can then go back through the backend setup to finalize everything. You should now see the card show up as an ATI TV Wonder and it should now be able to grab channels.

Happy TV watching!

---

