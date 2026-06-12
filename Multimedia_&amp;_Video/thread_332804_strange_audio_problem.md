---
title: "strange audio problem"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by ckellner on 2007-01-06
I have problem with my built in sound card on a gateway laptop with ubuntu 6.10

it did not work automatically, and the only way to get it to work is by running 

sudo modprobe -r snd-atiixp-modem
sudo modprobe snd-atiixp-modem

so it works immeadeatly after i enter the second line. I manage to block loading atiixp-modem module , so now i only have to enter the 2nd line.

Inititally, is suspected that the order of my sound cards are wrong, but i no matter if i assign to the modem -1 or 2 or whatever, it does not work.  The thing I don't understand> why do i need to load the modem-module - i dont intend to use modem sound.... 

any ideas? 
i am willing to post any command output you suggest....

Edit: finally solved the problem myself. after putting both snd-atiixp and snd-atiixp-modem to /etc/modules it seems to work

---

