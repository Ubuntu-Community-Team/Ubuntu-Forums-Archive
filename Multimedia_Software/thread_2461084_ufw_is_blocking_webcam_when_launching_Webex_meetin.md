---
title: "ufw is blocking webcam when launching Webex meeting app from browser"
date: 2021-04-24
forum: Multimedia Software
---

### Post by jfds2 on 2021-04-24
Good morning everyone,

My current OS is Ubuntu 16.04 LTS 64-bit. The current Firefox version is 87.0.

I have been experiencing a problem with the Webex meeting app that is launched from Firefox. The problem is that I cannot receive or emit video from my laptop's webcam. I can hear everyone OK, they can also hear me, and I can see presentations and interact with meeting attendees. _The problem is only the video_. This is not a huge problem, but my boss gets a bit nervous when he cannot see me. So I want to get to the bottom of this.

I have already installed the Cisco Webex extension on Firefox, installed ubuntu-restricted-extras as recommended by the Cisco Webex help center, troubleshoot my webcam with command ```
sudo modprobe -v uvcvideo
```. 

My Webcam has no issues, installing ubuntu-restricted-extras was a waste of time. Yet the video still does not work on the bloody Webex browser app ](*,). 

The good news is that I think I found the solution. When I disable ufw, everything works fine. Except that I had to disable the ufw. I was digging on the "[Webex Meetings Web App Known Issues and Limitations]("https://help.webex.com/en-us/n0rqd8g/Webex-Meetings-Web-App-Known-Issues-and-Limitations")" for clues about this, and I could find that Webex video uses ports UDP 9000 and TCP 5004. I immediately included these rules in my ufw but again went back to the frustrating video issue. 

So I am calling the forum for some help here.

Thanks in advance for your attention. I could not find a similar thread. My apologies if this has been already solved.

Best Regards,

---

### Post by CelticWarrior on 2021-04-24
Welcome.

Ubuntu 16.04 will be EoL in a matter of days. There's no point in troubleshooting.

---

### Post by jfds2 on 2021-05-01
Thank you CelticWarrior. You are right. So I upgraded to Ubuntu 18.04.05 LTS.

And  I finally found a solution to my problem. The problem was very silly  actually. It turns out I was using the wrong command to allow ports UDP  9000 and TCP 5004. With commands ```
sudo ufw allow out 5004/tcp && sudo ufw allow out 9000/udp
``` the camera is emitting video and I can see everyone ok. The 'out' part in the syntax is important. Perhaps there is a more secure way to do this? 

I hope this is helpful to someone

---

