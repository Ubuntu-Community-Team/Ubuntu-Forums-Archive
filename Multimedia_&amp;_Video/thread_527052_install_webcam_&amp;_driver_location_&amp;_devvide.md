---
title: "install webcam &amp; driver location &amp; /dev/video0"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by abuntu-handicapped on 2007-08-16
Does anybody know what webcam (in ubuntu 7.04) is 

1. easy to install
2. uses /dev/video0
3. can access the webcam driver
4. not too pricey (video and sound quality is the last of my worries)

This is a project for varsity and i was trying on a logitech pro 5000 but battling and am running out of time so am going to try a different webcam. Personal reviews would be better than a link to another discussion. A very important part of this is accessing the driver.

If anyone can suggest a possible w/c please also tell me how to access the driver once installed. (in lamens terms pls)

Looking forward to your responses.

---

### Post by dabl on 2007-08-16
What's the deal with the /dev/video0 device ID requirement?

Here's one that works out of the box: [http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/352&cl=us,en](http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/352&cl=us,en)

But I don't guarantee your specified device designation, as the USB bus dynamically assigns device IDs.  On my rig, the Hauppauge PVR-150 card is /dev/video0, and the webcam ends up wherever it ends up, depending on the other USB thingys I might have plugged in.

I don't use the webcam much, but I demonstrated it in Kopete for someone who was looking for one, so I know it does that much, plus I've captured a couple of stills from it when I was testing it.

HTH   :)

---

### Post by abuntu-handicapped on 2007-08-16
What's the deal with the /dev/video0 device ID requirement?

No deal really. just battling with all these programs that 'could not connect to video device (/dev/video0)' . it just seems that all web programs are looking at /dev/video0 and failing with pro 5000 hence my comment. I really dont care where it gets loaded as long as i can access the driver and it works as easily as 1-2-3

---

