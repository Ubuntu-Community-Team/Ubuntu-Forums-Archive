---
title: "Enable wireless greyed out"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by CommuneOfLoon on 2010-12-10
So I was going to post the following question because the "Enable Wireless" wasn't working. Instead, I figured out he accidentally turned the wireless switch off (Fn+F2). Just thought I'd still post this in case somebody has the same issue as below:

Okay, so I'm asking this question because my father's wireless stopped working suddenly; I don't live in the same city as him, so hopefully this doesn't get too messy :)

His wireless connection was working fine. I had installed Broadcom STA wireless driver via Hardware Drivers and it worked for three or four weeks. The other day he put the computer (Dell Inspiron 9400) to sleep but it wouldn't start up so got the power button. When he started it up again, his wireless was no longer working, specifically the "Enable Wireless" button is greyed out; Enable Networking is checked. The driver is still currently activated.

I was reading around, and found the sudo ifconfig wlan command and had him enter it. The output was:

    wlan0   Error fetching interface information: device not found

For sudo iwconfig wlan0
    wlan0   No such device

Just ifconfig seems to give normal readouts for eth0 and lo (normal in that they are similar to my computer's output).

The iwlist only gives outputs for eth0 and lo, no wlan0.

I have no idea how to guide him from here, any info or advice would be helpful. Thanks.

---

