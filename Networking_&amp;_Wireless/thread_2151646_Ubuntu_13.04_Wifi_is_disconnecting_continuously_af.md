---
title: "Ubuntu 13.04 Wifi is disconnecting continuously after undefined period on Laptop."
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by cforput on 2013-06-05
I have a very similar problem. The only difference is that I'm not in a campus environment. This is happening at home on my single router. I have yet to try wicd or ndiswrapper and was hoping that I could fix this without doing that.

I have created the log file but I don't know how to read it to see what might be the problem. Can anyone help?

---

### Post by varunendra on 2013-06-05
> **cforput said:**
> I have a very similar problem. The only difference is that I'm not in a campus environment. This is happening at home on my single router. I have yet to try wicd or ndiswrapper and was hoping that I could fix this without doing that.

I have created the log file but I don't know how to read it to see what might be the problem. Can anyone help?

You shouldn't need ndiswrapper. Are you using WPA/WPA2 mixed mode in router? It is recommended to use pure WPA2/PSK (AES) encryption, so change that in the router if it is currently set at mixed mode.

Apart from that, please try -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=Y fwlps=N
```
Then try to connect (do not reboot as the change will be lost on reboot) and see if the connectivity is any better.

---

### Post by s.fox on 2013-06-05
Posts moved to own thread as you are running a different version of ubuntu. Please do not hijack other peoples threads :)

Thank you.

---

### Post by cforput on 2013-06-05
S.Fox
Sorry didn't mean to barge in.

Varun,
I have a Belkin router and here are the settings

Security Mode: WAP/WAP2-Personal(PSK)
Authentication: WAP-PSK + WAP2-PSK
Encryption Technique: AES
Obscure PSK is checked

Options for each of the above are in addition to what I have already listed for each setting:
Security Mode: 
   Disabled
   128Bit WEP
   64Bit WEP
Authentication:
   WAP-PSK
   WAP2-PSK

I haven't tried the modprobe stuff yet because I want to get my router setting correct first. Can you suggest how I should set up each setting. It sounds like the Authentication should be set at WAP2-PSK but I'm not sure about the security mode.

---

### Post by varunendra on 2013-06-05
You guessed it right. Go with-> **cforput said:**
> 
Authentication:
   [s]WAP-PSK[/s]
   WAP2-PSK
Rest of the settings are good (AES, PSK).

And yes getting the router setting right is more important. The current one (Authentication: WAP-PSK + WAP2-PSK) is more than often problematic.

The modprobe commands I suggested are 'supposed' to help in some cases, but not necessarily. But since they are temporary (will be lost at reboot), you can safely try them anytime you wish. If they don't help connection, they shouldn't affect it adversely either.

---

### Post by cforput on 2013-06-06
Well, at the risk of Murphy's Law striking my wifi down, I have to say that I changed to WAP2 and have had better connectivity. I haven't tried the modprobe command yet but will keep it handy for the next time I have connectivity issues.

I'm also going to leave this open for a while longer before I mark it as solved in case my issues crop up again.

---

### Post by varunendra on 2013-06-06
> **cforput said:**
> Well, at the risk of Murphy's Law striking my wifi down,..... I'm also going to leave this open for a while longer before I mark it as solved in case my issues crop up again.
It may help a lot if you also keep your fingers crossed during this period *(I know cuz I do that very often after posting a suggestion..)* :P

---

### Post by bitstocoins on 2014-04-02
Same problem here 

there is a number of different things to try 


here is how i fixed the problem 

in terminal

```
 iwconfig wlan0
```

your output 


```

wlan0     IEEE 802.11abgn  ESSID:"YOURSSID"  ACCESSPOINT INFO   
          Bit Rate=58.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
         _** Power Management:on**_
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0
```

notice the power management on

if you see that here is how you fix this problem

again in terminal

```
 sudo iwconfig wlan0 power off
```

your new output
```

wlan0     IEEE 802.11abgn  ESSID:"YOURSSIDl"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: YOURACCESSPOINT   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
         _*** Power Management:off***_
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:106  Invalid misc:29   Missed beacon:0

```


Notice power management is now off

This is caused by laptops excessive efforts to save power.

This worked with a dell laptop

latitude e6410

ubuntu 12.04 lts 64bit


do not waste your time with 

```
sudo touch /usr/lib/pm-utils/power.d/wireless 
```

or 

```
sudo touch /etc/pm/power.d/wireless
```

those solves do not work

:KS

---

