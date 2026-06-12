---
title: "using kismet without getting disconnected from internet"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by obscurant1st on 2010-12-03
Is there anyway I could use KISMET without getting disconnected from a network. I mean now whenever I start kismet, I lose my network connectivity. I dont want that. is there any possible workaround for this? :O

---

### Post by chili555 on 2010-12-03
Kismet needs for your wireless card to be in Monitor mode. That means listen only and switch between all available channels.

Your internet connection needs the router or other access point to manage your wireless card; that is, determine what channel to stay on, negotiate the bit rate and other variables. Your card needs to listen and speak. That's called Managed mode.

I am not aware of any mechanism to do both simultaneously. You might be able to use two separate wireless cards, however. I imagine this is possible but difficult.

---

### Post by obscurant1st on 2010-12-03
oh i see. So its better to use a wired conection for internet and wifi for monitoring! :|

---

### Post by chili555 on 2010-12-03
> **obscurant1st said:**
> oh i see. So its better to use a wired conection for internet and wifi for monitoring! :|You could certainly try that. It will be a bit complex but, I imagine, not impossible. Network Manager is designed to shut off wireless if wired is available, so it may take a bit of fiddling. 

I have not tried this, so I can't be of much assistance.

---

