---
title: "Nova-t 500 remote Going round in circles"
date: 2009-11-19
forum: Mythbuntu
---

### Post by TomGar on 2009-11-19
Hi there

My Kosmic upgrade has knocked out my nova-t 500 remote

If I run lircd with this command
sudo lircd -H dev/input -d /dev/input/event7 -n
i can get irw to work and see the good old output

000000008001006c 00 Down hauppauge_nova_t_uk
000000008001006c 00 Down hauppauge_nova_t_uk
000000008001006c 00 Down hauppauge_nova_t_uk
000000008001006c 00 Down hauppauge_nova_t_uk

If I run lircd with this command
sudo lircd -n /etc/lirc/hardware.conf

i get these messages
lircd-0.8.6[9701]: error in configfile line 4
lircd-0.8.6[9701]: reading of file '/etc/lirc/hardware.conf' failed
lircd-0.8.6[9701]: reading of config file failed
lircd-0.8.6[9701]: lircd(default) ready, using /var/run/lirc/lircd

suggesting a problem with the conf file. (attached). This was diligently copied from [http://www.parker1.co.uk/myth/hardware.conf](http://www.parker1.co.uk/myth/hardware.conf) and simply modified to make the event number ok (and worked in jaunty etc)

So I'm now at a loss. I can see the remote working but the not in the proper way!

The mythbox is in an antec fusion case with an imon vfd running but since I can get this and the remote working as described above I think that may be a red herring.

Any help gratefully acepted.

---

