---
title: "Where does Monit get its' config in Mythbuntu 12.04?"
date: 2013-08-15
forum: Mythbuntu
---

### Post by krisbee2000 on 2013-08-15
This is very odd - I installed monit to make sure the backend is running - and with mythbuntu it is already configured to check mythbackend - but I would love to see how they have it configured, perhaps tweak it if it doesn't monitor the backend status page (which is better because that will determine when it is hung as opposed to not-existing) - however, when I check monitrc there is nothing in there and there is nothing in /etc/monit/conf.d as well - it is a mystery where it is getting its' config from! 

Can anyone help point me to where the monit is getting this default config from? I don't want to add my .conf that I have made (which works great, and it also checks mysql as well) because it is possible to spawn two copies of mythbackend then.

Thanks in advance!

---

### Post by tgm4883 on 2013-08-15
Mythbuntu doesn't have a Monit configuration that I know of. Where are you getting this information?

---

### Post by krisbee2000 on 2013-08-15
> **tgm4883 said:**
> Mythbuntu doesn't have a Monit configuration that I know of. Where are you getting this information?

Ah!  I feel like such an idiot!  I named my system mythserver, so when I saw the monit config page, it said system_mythserver running and didn't put it together that all it meant was that my system was running!  D'OH!

Thank you for just putting it in a way that made me connect the dots...

---

