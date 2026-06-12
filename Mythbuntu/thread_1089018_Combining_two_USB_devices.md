---
title: "Combining two USB devices?"
date: 2009-03-06
forum: Mythbuntu
---

### Post by Caps18 on 2009-03-06
I had an idea on how to solve one issue I have.  And it might be pretty simple to do.

I have two MCE remote IR receivers but I can only hook in one to the USB port at a time on my computer.  If I plug in both, neither works and the computer doesn't like it.

So, my idea is to buy the connectors to wire up a joiner.

[http://www.newark.com/jsp/search/productdetail.jsp?sku=84K7062](http://www.newark.com/jsp/search/productdetail.jsp?sku=84K7062)

I would have another connector to hook up one usb wire on the back of that part.  And I would join each of the four wires to the pair of wires coming in.

This way, the two IR remote receivers in the two rooms can send the signal to the computer, regardless of which room I am in.  

Does this make sense?  Do you think this will work?

---

### Post by Caps18 on 2009-03-27
So, I got all of the supplies and tested this out today.  It didn't work.  :(

I'm still not sure why.  And I'm not sure why I can't plug in both usb IR receivers into two ports and have them work.  Is anybody out there using two IR USB remotes?  :confused:  

I would be interested in hearing what you had to do to make them work.

---

### Post by theophile on 2009-03-27
All that does is add another USB port. If two devices don't work together when plugged directly into the mobo's USB ports, adding another port isn't going to solve the problem. Each device is still recognized as an individual device by the computer.

And why do you need two? Are you running two displays off the same frontend?

---

### Post by SiHa on 2009-03-27
Sorry, but wiring two USB connectors together just won't work.

Why don't you get an IR extender / repeater for your second room? This will relay the signal to the receiver and then on to your PC.

---

### Post by Caps18 on 2009-03-27
I'm running three displays off this front end.  The issue is the wireless IR extenders have some sort of interference problem and don't work very well.

I would like to get both upstairs rooms using their own hard wired USB IR reciever if possible.

---

### Post by theophile on 2009-03-27
Sounds like you may have to explore other options. Perhaps another frontend?

---

### Post by Caps18 on 2009-03-27
Maybe I should see if someone has done this over at the MythTV forum.  It is part of how the operating system and software handle two IR receivers though.

Are there any Unix commands to see what USB devices are there kind of like ifconfig?  I will have to look at the log files to see if anything is in there as well.

Adding a front-end wouldn't be totally out of the question (I have a spare computer from work that isn't doing anything, but will need a new video card), but I would rather do it as simple as possible.  And I'm not sure I would want to have the second frontend on all the time either since I only use it for an hour every other day.

---

### Post by theophile on 2009-03-27
Try 'lsusb'

---

