---
title: "Pulseaudio Multicast - very high bandwidth"
date: 2012-10-14
forum: Multimedia Software
---

### Post by zcacogp on 2012-10-14
Hello, 

I've started playing with Pulseaudio, with a view to using it to play the same music from several machines simultaneously. The machines are all running 12.04 and on a home WiFi network (54Mb/S). I am using paprefs to configure Pulseaudio on the various (client and server) machines and pavucontrol to change the various volume settings. 

Streaming from one machine to another works OK. Multicast (RTP) streaming to more than one machine doesn't, and I understand this is due to the network becoming bogged down with traffic; no sound comes from any machine and any other machine on the network - not doing anything sound-related - ceases to be able to access network resources. If I run the machines all plugged into a network cable it works after a fashion, but the sound is very choppy and hence it's not really usable. 

Some googling suggests that I am far from the only one to suffer this, but I can't find a solution anywhere. Is there one (other than putting network cables to every point in my house)? There is little else running over the network - in fact, there was nothing else running over the network when I tried this out. 

If you know how to overcome this problem then I'd love to hear how!

Thanks, in advance. 


Oli.

---

### Post by Cheesemill on 2012-10-14
I believe it's just a limitation of using a wireless network.

Because of the way a wireless network works only one device can transmit or receive data at a time.

---

### Post by zcacogp on 2012-10-14
Cheesemill, 

Thanks for your answer. I didn't know that wireless networks only allowed one device to send or recieve at any one time - thanks for telling me. Every day is a school day, eh? 

Does that mean that multicasting can only work on a wired network? 

I have found more information about configuring Pulseaudio, particularly concerning the sampling rate, here: 

[https://wiki.archlinux.org/index.php/PulseAudio#3._Setting_the_soundcard.27s_sampling_rate_into_pulse_audio_configuration](https://wiki.archlinux.org/index.php/PulseAudio#3._Setting_the_soundcard.27s_sampling_rate_into_pulse_audio_configuration)

Is this likely to help me at all? Probably not, given your comments about WiFi and the fact that I want to run it over WiFi ... 

Thanks again for your input. Am I simply trying to achieve the impossible? 


Oli.

---

### Post by borisboef2 on 2013-03-15
Hi, 

I am experiencing the same problems however I am using a wired network.

I'm running ubuntu 12.10 and as soon as I switch to my RTP multicast output device the latency on my network becomes massive/ unresponsive.

64 bytes from server (192.168.0.1): icmp_req=1 ttl=64 time=0.281 ms
64 bytes from server (192.168.0.1): icmp_req=2 ttl=64 time=0.300 ms
64 bytes from server (192.168.0.1): icmp_req=3 ttl=64 time=0.245 ms
64 bytes from server (192.168.0.1): icmp_req=4 ttl=64 time=0.240 ms
64 bytes from server (192.168.0.1): icmp_req=5 ttl=64 time=0.332 ms
64 bytes from server (192.168.0.1): icmp_req=6 ttl=64 time=0.303 ms
64 bytes from server (192.168.0.1): icmp_req=7 ttl=64 time=0.258 ms
64 bytes from server (192.168.0.1): icmp_req=8 ttl=64 time=1097 ms
64 bytes from server (192.168.0.1): icmp_req=9 ttl=64 time=1245 ms
64 bytes from server (192.168.0.1): icmp_req=10 ttl=64 time=959 ms
64 bytes from server (192.168.0.1): icmp_req=11 ttl=64 time=23272 ms
64 bytes from server (192.168.0.1): icmp_req=12 ttl=64 time=22263 ms
64 bytes from server (192.168.0.1): icmp_req=13 ttl=64 time=21255 ms
64 bytes from server (192.168.0.1): icmp_req=14 ttl=64 time=20247 ms
64 bytes from server (192.168.0.1): icmp_req=15 ttl=64 time=19239 ms
64 bytes from server (192.168.0.1): icmp_req=16 ttl=64 time=18231 ms
64 bytes from server (192.168.0.1): icmp_req=17 ttl=64 time=0.288 ms
64 bytes from server (192.168.0.1): icmp_req=18 ttl=64 time=0.299 ms


Did you find a way to fix this?

---

### Post by RobbieCrash on 2013-06-24
> **Cheesemill said:**
> I believe it's just a limitation of using a wireless network.

Because of the way a wireless network works only one device can transmit or receive data at a time.

Thank you very much for this post, it helped me quite a bit in improving performance. This is incorrect though; multicast over 802.11 networks is fully supported. In most networks it's performed by buffering all multicast packets at the access point and then sending packets after DTIM intervals. More information is available [here]("http://en.wikipedia.org/wiki/IP_multicast#Wireless_.28802.11.29_considerations").

I have had moderate success after tuning my wifi as suggested, as in, my network no-longer becomes completely useless when multicasting anymore; it's just super slow now.

---

