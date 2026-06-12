---
title: "Wi-Fi LED flickers and has a slow connection."
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by silkworm2.5 on 2010-10-08
Hi.

It has a button next to the power to show the wireless status, on or off. If I turn the laptop on with the wireless active, it keeps flickering between on and off states, and gives me a really slow connection.

It happened in 10.04 if I booted with the wireless activated, but could be fixed by resetting the wireless. Now in 10.10, it happens constantly, and I just wont stop. Can anyone help me please? :(

My laptop is a CompaQ Altec Lansing running 64 bit.

---

### Post by silkworm2.5 on 2010-10-10
**Bump**

---

### Post by ravi84m on 2010-10-14
i have also faced this issue after upgrading. the following trick did it for me though ```
sudo gedit /etc/modprobe.d/wlan.conf
```copy paste the  following line:```
options iwlcore led_mode=1
```save and restart.
it worked for me at least... good luck

---

### Post by silkworm2.5 on 2010-10-25
Yo.
Sorry I took so long to reply. I returned to 10.04 and forgot about this thread.

Unfortunately, the LED still flickers as it transfers data. I tried modifying the code to 0 and then 2, but neither of them affected the LED. Any advice on that please?

And the internet is still really slow. Not as bad as before but still really bad.

---

### Post by silkworm2.5 on 2010-10-26
**Bump**

---

### Post by ravi84m on 2010-11-07
have you actually tried just putting 1 instead of 0 or 2. then reboot.
this solution works only for the blinking wifi led. as for internet speed im afraid i have no idea how to solve this... could it be a hardware issue?

---

### Post by silkworm2.5 on 2010-11-08
Yes I did reboot after each edit. Still no luck. And I have no Idea if it's a hardware issue. Do we get a different linux Kernel with 10.10? Because thats all I can think of that would cause the connection speed error.

---

### Post by ravi84m on 2010-11-10
I also had some issues with 10.10 that i didn't in 10.04 so it's probably related t the kernel. you might want to upgrade to the latest kernel or even downgrading to the one you found the most stable if you're that desperate.

---

### Post by silkworm2.5 on 2011-05-30
Well, after half a year and using 10.04 I fixed the main problem.
I stayed with 10.04 until 11.04 was released and didn't look back at 10.10. Unfortunately, I still had connection issues with 11.04 too!
So this time I installed the drivers from here: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
And this solved the wireless problems for me in 11.04! After this I decided to go back to 10.10 on a live USB to try and fox it. It took me around 3 minutes to fix a problem I had been ignoring for 6 months XD

I am posting this message to hopefully help others with similar troubles and to mark this thread as solved.

---

### Post by me_loco on 2011-06-05
could anyone help me?
i have the exact same issue with 11.04 thinkpad T61.
LED light blinking and wireless connection slows down gradually.
I'm completely new to ubuntu, i came from opensuse where i didn't have wireless connection issues.

could you please provide steps on how to update wireless driver?

here is my wireless hardware
Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Thank you.
I like ubuntu unity and i don't want to leave it.

---

### Post by me_loco on 2011-06-05
Anyone willing to help?

---

### Post by silkworm2.5 on 2011-06-13
Sorry, I didn't check back here for responses. Sure, I'll help you.
(BTW, sorry if this sounds patronising at all.)

First, go [here]("http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball") and download the compat-wireless-2.6.tar.bz2 file. After it is downloaded, extract it.

I'm going to assume that the Download location is the "Downloads" folder in your home folder. To install the drivers we're going to need to use a terminal.
In Unity, go into the dash, and search for "Terminal". you should get a purple box with your username in it.

In this box type in this command:
```
cd ./Downloads/compat-wireless-2011-06-01/

```
This will **C**hange **D**irectory to the folder the drivers are in.

Next we want to run the command:
```
./scripts/driver-select iwlagn
```
This will then generate the installation scripts and backups of existing drivers.

Next we want to run:
```
make
```
And then:
```
sudo make install
```
(Any command with "sudo" at the start is an administrative command, and so will ask for your password)

The drivers should now be installed! However, you have to tell Ubuntu to start using them. so the last two commands you will need to use are:
```
sudo make unload
```
(Will disconnect your Bluetooth, Ethernet and wireless connections, don't do this if you're doing something important with them.)
```
sudo modprobe iwlagn
```
(This command will restore the connections using the new drivers.)

That should fix your problems! It didn't fix my LED issue, but you might have better luck. It did at least, fix the slowing connectivity issues I had.

If you find that after this you cannot connect to any networks after this, run the following commands to revert to the default drivers:
```
./scripts/driver-select restore
make
sudo make install
sudo reboot
```

I hope this helps and that I wasn't too late :)

---

