---
title: "Mobile Broadband &amp; 8.10"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by frankwakeman on 2008-12-15
I've had Ubuntu 8.10 on my Toshiba Equium laptop a couple of days, overcome most difficulties now and am thinking of undoing my Wubi install and doing a dual boot setup properly or even getting rid of Windows altogether.  But, Mobile Broadband is a bit weird, randomly asking for a keyring password and not accepting what I enter when it does.  So I'm sending this through Vista for the time being.

I'm surprised it isn't simpler to do away with passwords altogether as I live alone and use this machine alone and don't have to use a password with Vista, though Vodafone uses 'web' in its default settings, which I've used.

It often works, it just seems a random problem.  Can anyone help me get some consistency or tell me how the problem isn't random and suggest what I'm doing wrong.

My USB dongle is a Huawei K3520, as badged by Vodafone (it has another name but I've forgotten what).

Also is there a meter I can use for Mobile Broadband.  I downloaded two through Synaptic (Etherape and Knet-something) but they only dealt with ethernet.  I get 3gb a month with Vodafone so it is an important thing to watch.

Thanks.

---

### Post by spy_1134 on 2008-12-15
This is often a problem with your keyring

Acess your Ubuntu partition through Vista and delete /home/<username_here>/.gnome2/keyrings/default.keyring

Replace <username_here> with your system username

Start up Ubuntu and try connecting to your wireless, it should prompt you to make a new keyring and set the password.

Hope this helps

---

