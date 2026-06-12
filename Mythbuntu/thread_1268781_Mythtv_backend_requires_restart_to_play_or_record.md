---
title: "Mythtv backend requires restart to play or record"
date: 2009-09-17
forum: Mythbuntu
---

### Post by Dragonflyoh on 2009-09-17
I have Mythbuntu 9.04. When I reboot the machine I cannot view live TV with the front end until I stop and restart the backend. When I run the front end and check system status I get an error message that says there is a problem with capture cards Card 1 failed init. Get the same error for card 2. I did some searching and found recommendations to change the settings in etc/rd5.d to s99mythtv-backend and did that. It has not helped. Any ideas would be appreciated.

---

### Post by joho500 on 2009-09-18
I think you have to change it in /etc/rc2.d because that's the runlevel ubuntu runs in.

Cheers, 
Joost

---

### Post by Dragonflyoh on 2009-09-18
That was the cure!! Thank you so much!

---

