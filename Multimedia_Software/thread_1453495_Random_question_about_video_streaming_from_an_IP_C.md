---
title: "Random question about video streaming from an IP Camera"
date: 2010-04-13
forum: Multimedia Software
---

### Post by prupert on 2010-04-13
Hi

This is probably the wrong forum to star and I am clutching at straws here hoping someone can point me in the right direction.

I own a cheap IP Network WebCam, bought from eBay (like this one:
[http://cgi.ebay.co.uk/WPA-Wireless-WiFi-IP-Camera-CCTV-PT-Webcam-new-freeship_W0QQitemZ110518953881QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item19bb716799](http://cgi.ebay.co.uk/WPA-Wireless-WiFi-IP-Camera-CCTV-PT-Webcam-new-freeship_W0QQitemZ110518953881QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item19bb716799)) that looks like this:

[IMG]http://i298.photobucket.com/albums/mm275/milycai/300-3.jpg[/IMG]

it doesn't list it's manufacturer anywhere and just says it is the F-Series IP Camera.

It works well, both on Firefox and IE. However, you can only get a live video stream with audio out of it using IE and an ActiveX plugin or the supplied Windoze only IP Camera Super-Client software which doesn't like Wine. 

As I am mainly an Ubuntu user, I was wondering if anyone knew of any tricks to get hold of the two streams, maybe using VLC to view?

I've tried IE4Linux and Play-On-Linux to install IE in ubuntu, but the ActiveX unsurprisingly doesn't work. I was hoping that:

[LIST=1]
[*]someone can point me to a forum that might have someone who knows
[*]someone can tell me how to analyse the network traffic that IE is getting to get an IP address for the video and audio feeds
[*]someone has some experience with these cameras and knows the answer to all my questions ;)
[/LIST]

I've tried using wireshark, but the output makes no sense to me - I've figured out various addresses to the video stream:

[http://192.168.1.126:81/videostream.cgi](http://192.168.1.126:81/videostream.cgi)
[http://192.168.1.126:81/video.cgi](http://192.168.1.126:81/video.cgi)

But I can't get the audio stream. I was hoping to use it as a baby monitor, it has excellent night viewing capabilities with its IR LEDS, but having no audio in Ubuntu with it is a pain.

Any suggestions? It's a long shot I know.

---

### Post by mommfried on 2010-04-24
Hello,  

i got my cam here:  [http://www.dealextreme.com/details.dx/sku.26358](http://www.dealextreme.com/details.dx/sku.26358)  there you will find links for firmware for getting Firefox support, it works for me. 
I didn't test sound until now, because it's not importend for me, but getting the stream in vlc is no problem, in my case with  [http://192.168.1.28:9008/videostream.cgi](http://192.168.1.28:9008/videostream.cgi)  
I don't use wireshark for that, i just rightclick on the stream in Firefox and get grafik-info ;-)  

Regards  

Momme

---

### Post by prupert on 2010-04-24
Thanks for the reply, very interesting. It seems my camera came with that firmware already.

It works fine in firefox and VLC, just wish I could get the audio out of it as well ;)

---

