---
title: "difficulties getting lirc to transmit with ir blaster"
date: 2008-11-01
forum: Multimedia Software
---

### Post by astrand on 2008-11-01
Hi All,
This is on a fresh install of 8.10.  I added an additional PVR-150 and am trying to control a STB (Hughes GAEBO).  I already have an RCA box working fine through a direct serial connection.  The RCA box also works fine through either of my external RS232 ports (ttyS0 or ttyS1).  Because the Hughes box has no facility for direct connections, I bought an ir blaster from [www.irblaster.info](www.irblaster.info).  I installed lirc using apt-get and used dpkg-reconfigure to set it up (many times at this point).  Regardless of which port I use in the configuration, I cannot get lirc_serial to send codes to the blaster.  In dpkg-reconfigure, I select 'none' for the remote and 'serial directv' for the transmitter.  

I'm testing using irsend.  lircd is not crashing or complaining in the messages log.  dmesg indicates that lirc_dev and lirc_serial are set up (I think correctly by comparing to messages others have posted).  This is not an issue with the lircd.conf file as far as I can tell, because there is _no_ ir information produced by the ir blaster at all.  I used the digital camera approach to confirm this last statement.

My understanding is that in previous releases lirc_serial was not set up correctly for transmission by the configuration process.  Is this still the case?  Is there a workaround?

Thanks,
astrand

---

### Post by astrand on 2008-11-06
bump

---

