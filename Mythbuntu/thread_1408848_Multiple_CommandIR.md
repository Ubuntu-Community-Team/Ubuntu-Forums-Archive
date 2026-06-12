---
title: "Multiple CommandIR"
date: 2010-02-16
forum: Mythbuntu
---

### Post by vivekg on 2010-02-16
Hello,

I am trying to setup multiple instances of CommandIR on my system. But it only seems to send commands to one instance. Has anyone tried this before? Any help/pointers would be greatly appreciated.

Vivek

---

### Post by commandir on 2010-02-17
To send to specific emitters on the first CommandIR:

irsend send_once commandir settransmitters-1
irsend send_once (remote_name) (remote_button)
irsend send_once .... 

irsend send_once commandir settransmitters-2
irsend send_once (remote_name) (remote_button)
irsend send_once .... 

irsend send_once commandir settransmitters-3
irsend send_once (remote_name) (remote_button)
irsend send_once .... 

irsend send_once commandir settransmitters-4
irsend send_once (remote_name) (remote_button)
irsend send_once .... 

To send to specific emitters on the second CommandIR:

irsend send_once commandir settransmitters-5
irsend send_once (remote_name) (remote_button)
irsend send_once .... 

irsend send_once commandir settransmitters-6
irsend send_once (remote_name) (remote_button)
irsend send_once .... 

irsend send_once commandir settransmitters-7
irsend send_once (remote_name) (remote_button)
irsend send_once .... 

irsend send_once commandir settransmitters-8
irsend send_once (remote_name) (remote_button)
irsend send_once ....

---

