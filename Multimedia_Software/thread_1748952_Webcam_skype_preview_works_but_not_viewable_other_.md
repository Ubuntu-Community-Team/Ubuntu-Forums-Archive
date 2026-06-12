---
title: "Webcam skype preview works but not viewable other end"
date: 2011-05-04
forum: Multimedia Software
---

### Post by rapattack1 on 2011-05-04
My webcam works at my end but two people have said they can't see me their end using skype. They webcam with other people so i know it is not their settings or anything. One has a mac and the other a windows machine. I really don't have anyone else to test this with as most people i know don't have webcams. I haven't heard of this problem before so would appreciate some advice :0)

---

### Post by rapattack1 on 2011-05-26
Hi please if there is anyone that has heard of this problem?????

---

### Post by rapattack1 on 2011-06-05
Hi is this a permission issue? Just occured to me that maybe this is the problem as to why people can't see my webcam> As i can't remember anything to do with permissions i thought i would ask

---

### Post by shreepads on 2011-06-05
Stupid question, but when you say "My webcam works at my end", is it working in the Skype -> Options -> Video Devices, in the Test window to the right or do you mean its working in some other app like Cheese.

The output from lsusb listing your device will help as well...

---

### Post by rapattack1 on 2011-06-05
Hi yes works in that test window in Skype and cheese. Also a few other apps as well. Just also hooked it up to my windows machine and it is woking with skype. The other party i am talking to can see an image ...i won't say of me because the camera is running as a security camera outside. One person said they can see that outside image. I had a previous install of ubuntu and everything was working well then. It was a 32 bit system as is the machine that is running windows. Oh i thought i did the lsusb thing. I can't do it right now as the webcam is hooked up to the windows machine and i am on skype.

---

### Post by pierreu1 on 2011-06-05
Exactly the same problem as the original poster.

Bus 004 Device 003: ID 2222:3085 MacAlly 

In the test area on Skype it lists a usb20 camera (/dev/video0).

When I test, nothing occurs, but all things are working in Cheese. I use to have MAverick and it worked then well!

Please help! It has been a month!

Thanks!

---

### Post by beew on 2011-06-06
Hi,

When you make a connection  there is a box in the bottom of the Skype video screen that looks like a camera, right click it and check that "enable video" or something like that is actually ticked. It may sound stupid but I had the same problem at first and then I realized the option was actually unchecked.

---

### Post by rapattack1 on 2011-06-06
beew-can you tell me where that is...can you do an image capture of it please. I saw something like that in the windows version i think but not the linux version of skype so i am curious. I get the preview anyway but the people that i am talking to on skype(my contacts) cannot see me on video....seems no one has a solution or has the same problem. I know it is not the camera as i have it on my windows machine now and it is working well.

---

### Post by beew on 2011-06-08
> **rapattack1 said:**
> beew-can you tell me where that is...can you do an image capture of it please. I saw something like that in the windows version i think but not the linux version of skype so i am curious. I get the preview anyway but the people that i am talking to on skype(my contacts) cannot see me on video....seems no one has a solution or has the same problem. I know it is not the camera as i have it on my windows machine now and it is working well.

I am sorry, I can't give you a screen capture because you can only see that when you are actually having a video chat with someone. Anyway it is the box with the camera shape icon under the Skype screen.

---

### Post by rapattack1 on 2011-06-08
OK thanks i really don't know what the skype screen is but i will look for this when i have the camera back attached. It is attached to the windows machine for security camera purposes and when i get the proper camera for that purpose that i bought from ebay from overseas then i can change things around. I have it wired around so many things to the outside of my place that it is way too hard to bring inside or replug into another machine :0)

---

### Post by fulltimer5 on 2011-06-08
I've had same problem for weeks on all ubuntu flavors. Lost camera when upgraded from 9.10 finally thruout skype 2.2, and reinstalled skype 2.1.0.81 and all problems solved:KS

---

### Post by rapattack1 on 2011-06-08
Yeah i might try but i can see the webcam this end...just the other party can't see me. So far no one has said they have this same problem :0(

---

### Post by beew on 2011-06-08
Ok, I got a screenshot. I got the button to show by calling the echo testing lady.

See where the cursor is? When you are in a video chat click that and choose "Share My Video"

---

### Post by rapattack1 on 2011-06-09
Oh ok thanks for that screen shot. Ok don't have it now maybe because the webcam is not plugged in. Will let you know. Hopefully will get the other camera soon :0)

---

### Post by rapattack1 on 2011-06-17
Hi i just plugged in my webcam again after receiving my security camera and having that running smoothly. The webcam is still the same...issue wise. I looked at when initiate a call and there is no button to select for video. Does that appear after the call has been accepted or the button is there as soon as that windows pops up? Thats odd if so because i can remember just selecting enable video in the options would make skype attempt a video connection straight away. Just remembered that. It even has those things selected to do so in the options so i don't see how you would have to enable during a call? Anyway either way this is not working :0(

---

### Post by beew on 2011-06-17
> **rapattack1 said:**
> Hi i just plugged in my webcam again after receiving my security camera and having that running smoothly. The webcam is still the same...issue wise. I looked at when initiate a call and there is no button to select for video. Does that appear after the call has been accepted or the button is there as soon as that windows pops up? Thats odd if so because i can remember just selecting enable video in the options would make skype attempt a video connection straight away. Just remembered that. It even has those things selected to do so in the options so i don't see how you would have to enable during a call? Anyway either way this is not working :0(

The button appears after the call has been accepted. But as you said you can set it up automatically. Go to options > video device and check the box to enable video by default.

---

### Post by rapattack1 on 2011-07-08
Yep that is done. I have always checked those boxes in skype to get video. Sad that it does not work in this distro version whatever. Anyway i have given up.

---

