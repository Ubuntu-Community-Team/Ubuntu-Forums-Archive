---
title: "atheros AR928X wireless is disabled by hardware switch"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by idelibashev on 2012-02-05
Hi all,

I have this problem since several days. I tried what i have found through forums but nothing helped.

Here are details:
I am using ASUS X50Z laptop with AR928X wireless adaptor.
Linux version is Ubuntu 11.10

When pressing Fn+F2 nothing happen. Only switching between Soft blocked on/off. Hardware is always blocked. I can't find a way to unblock it.

It matter of "life and death" situation here. Please, help

---

### Post by idelibashev on 2012-02-06
Hi all,

Can someone help me here?
I am really desperate

Thanks in advance

---

### Post by chili555 on 2012-02-06
Please run and post:```
rfkill list all
lsmod | grep asus
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by idelibashev on 2012-02-06
The output is:
> 0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

asus_laptop            19050  0 
sparse_keymap          13658  1 asus_laptop


As I said, I coldn't find a way to change hard blocked to 'no'

---

### Post by chili555 on 2012-02-06
Please try this:```
sudo rmmod -f asus-laptop
sudo rfkill unblock all
rfkill list all
```Any improvement?

---

### Post by idelibashev on 2012-02-07
No.
Soft blocked: no
hard block: yes

---

### Post by chili555 on 2012-02-07
Let's write one file to try to make it work:```
sudo gedit /etc/modprobe.d/asus-laptop.conf
```Add one line:```
options asus-laptop wlan_status=1
```Proofread carefully, save and close gedit. Reboot and check:```
rfkill list all
```I realize '=1' is the default, however something is decidely wrong here.

---

### Post by idelibashev on 2012-02-07
Thanks, chili555, for your help, but so far no results :(

Still hard blocked is 'yes'

Is there a way to check that this is not a hardware problem?
I notice that switching ON/OFF with Fn+F2 doesn't change the light to bluetooth. It i salways on for wireless

---

### Post by chili555 on 2012-02-07
Please check:```
cat /sys/class/net/wlan0/device/rfkill/rfkill0/state
```The result is probably 0. If so, please do:```
sudo su
echo 1 > /sys/class/net/wlan0/device/rfkill/rfkill0/state
exit
```Now check:```
rfkill list all
```> Is there a way to check that this is not a hardware problem?You might check if the kernel recognizes the key presses:```
sudo tail -f /var/log/syslog
```Is there any recognition of the Fn+F2 key? Get out of 'tail' with Ctrl+c.

---

### Post by idelibashev on 2012-02-08
There is no such file: /sys/class/net/wlan0/device/rfkill/rfkill0/state

In syslog there is no trace for pressing Fn+F2

Regards
Ivan

---

### Post by chili555 on 2012-02-08
> /sys/class/net/wlan0/device/rfkill/rfkill0/stateHow about:```
cat /sys/class/rfkill/rfkill0/state
```Thanks.

---

### Post by idelibashev on 2012-02-09
Yes, i have that file, but the value is '2' and I am not able to change it to 1

Thanks

---

### Post by chili555 on 2012-02-09
I am sorry; I am out of ideas. I wish I could be more helpful.

---

### Post by idelibashev on 2012-02-09
thank you anyway

---

### Post by idelibashev on 2012-02-13
Well, thats embarrassing. It turned out that someone from my family was switched off the wireless by a hardware switch on the left side of the laptop. Once I switched it to ON the wireless worked.

Thanks for the help

---

### Post by chili555 on 2012-02-13
I'm glad it's working by whatever means. Have fun!

---

