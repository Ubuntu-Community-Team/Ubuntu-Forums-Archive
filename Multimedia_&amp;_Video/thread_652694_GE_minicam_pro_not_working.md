---
title: "GE minicam pro not working"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by Tanjer1588 on 2007-12-29
I have  GE MiniCam Pro HO98656, 98067/98756, gos b another name i think too, but thats not that point. I cant find any drivers at all on the internet, nothing works for it. I dont know if the cam even is being detected. It has a built in mic and i think it worked on here before but i have not tryed it in a while. the cams getting power but i dont know if its being picked up by Ubuntu at all, so any kind of help would be nice thank you.

ps. there was another post like this about 4 weeks ago by me, but never got anwserd and told me to use easycam pro, i reposted cus i want to know if my cams even being detected and then see if i can get it to work.

---

### Post by linuxwizard on 2007-12-29
in terminal > lsusb > will list any connected USB devices > post results

---

### Post by Tanjer1588 on 2007-12-29
Here are my resaults of lsbus

```

Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0c45:60fe Microdia 
Bus 001 Device 001: ID 0000:0000 

```

Then i unpluged my cam

```

Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

Pluged it in again
```

Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0c45:60fe Microdia 
Bus 001 Device 001: ID 0000:0000 

```

So im takeing that the 0c45:60fe Microdia is my cam, now that i know that what would be my next step?

thank you again

---

### Post by linuxwizard on 2007-12-29
Yes this is your webcam > Bus 001 Device 006: ID 0c45:60fe Microdia > I was looking around trying to find which driver you need could not come up with anything. Does not mean their is not one. I would suggest trying EasyCam see if it will find a driver for you.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Tanjer1588 on 2007-12-29
so i tryed easy cam, didnt find one for me, but theres an easycam2 out now, so i can try that one too see if it works, do you know anything els other then easy cam that can do the same thing?

---

### Post by linuxwizard on 2007-12-29
You should have just tried EasyCam2 first. No I don't know of anything else you can try besides EasyCam.

---

### Post by Tanjer1588 on 2007-12-30
Bumb, looking for drivers for my came, if anyone knows of any just let me know

---

### Post by Tanjer1588 on 2007-12-31
bump for great justice

---

### Post by linuxwizard on 2007-12-31
I have found a few post on Microdia webcams they say the driver from here works. I am not sure what you are to use but maybe you can figure it out. Good Luck

[http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

https://groups.google.com/group/microdia

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:8105

---

