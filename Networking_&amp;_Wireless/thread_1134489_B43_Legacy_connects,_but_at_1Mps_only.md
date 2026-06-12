---
title: "B43 Legacy connects, but at 1Mps only"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by Guitarmaster316 on 2009-04-23
Hi all,

I have an HP ze4560 with a Broadcom 4306 (rev2) card and Jaunty (9.04)

I can connect to netowrks, but it is very slow and drops the connection sometimes.

I have tried...

sudo iwconfig wlan0 rate 54M fixed
sudo iwconfig wlan0 rate 11M fixed
sudo iwconfig wlan0 rate 54M
sudo iwconfig wlan0 rate 11M

When I do this I get no change in the speed (even though it shows different in iwconfig.

I have also tried ndistk in syaptic manager and installed the windows driver, but NOTHING happened when I did that.  Yes, I have both the .inf and .sys files in the same folder.

I am a recent Windows convert and I love everything about Linux... except the fact I can't seem to get my wireless to work at the proper speed.

Can anyone help???

Thanks,

Matt

---

### Post by ausmuso on 2009-04-23
> **Guitarmaster316 said:**
> Hi all,

I have an HP ze4560 with a Broadcom 4306 (rev2) card and Jaunty (9.04)

I can connect to netowrks, but it is very slow and drops the connection sometimes.

I have tried...

sudo iwconfig wlan0 rate 54M fixed
sudo iwconfig wlan0 rate 11M fixed
sudo iwconfig wlan0 rate 54M
sudo iwconfig wlan0 rate 11M

When I do this I get no change in the speed (even though it shows different in iwconfig.

I have also tried ndistk in syaptic manager and installed the windows driver, but NOTHING happened when I did that.  Yes, I have both the .inf and .sys files in the same folder.

I am a recent Windows convert and I love everything about Linux... except the fact I can't seem to get my wireless to work at the proper speed.

Can anyone help???

Thanks,

Matt

I had this problem with Intrepid too, Matt, be it with a different wireless chip. I found I could get a perfect connection under OpenSuSE 11.0 with the commands:
   su
   iwconfig wlan0 rate 36M

However, when I tried:
   sudo iwconfig wlan0 rate 36M

under Ubuntu Intrepid, nothing appeared to happen.

I did find I could get the right result by issuing the command twice, with a few seconds in between. Then, if I closed the terminal window and rightclicked the connection icon on the top taskbar, it DID show up as running at 36M! I've done some massive download since, and I haven't had problems.

I'm still wondering about the why and how, though, maybe someone can enlighten me.

---

