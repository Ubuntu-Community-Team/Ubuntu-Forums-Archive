---
title: "Create a new master backend or a slave?"
date: 2013-06-02
forum: Mythbuntu
---

### Post by Erik-NA on 2013-06-02
Hello

I have installed a master backend (DVB-S with HD-channels) for usage at my ordinary home. Now I am investigation how to install a second backend (DVB-S also with HD-channels) at my vacation home. Both houses are fiber connected to the Internet. The bandwidth is 100 Mbit/s to my vacation home and 10 Mbit/s the other way.

Since I am watching HD channels there should be bandwidth limitations when watching a liveTv HD-channel from a frontend in my ordinary home which is streaming live Tv from the slave backend on my vacation home? I recon a HD-channel takes between 20-30 Mbit/s?

I want my frontends to connect to the backend which is residing on the same physical location. So can a frontend connect to a slave backend or must all frontends connect to the master backend?

---

### Post by klc5555 on 2013-06-02
Frontends connect to the master backend, where the database lives. Content which happens to have been recorded on a slave backend (because the master backend told it to), when played back will normally get streamed to the master backend, and from there to the requesting frontend. 

So unless your vacation home is located in the back yard of your main home, I think you'll need a completely independent master backend in each residence. Since each of the two master backends will be sitting behind its own router on its own local intranet, you can give each of the two the same workstation name and the same local static IP address, enabling your mobile frontends to connect with the master backend in whichever residence they happen to be without changing any settings. However, recorded content will not be shared between the two backends.

---

### Post by Erik-NA on 2013-06-02
Many thanks for the clarification!

Then I am going to install two master backends.

Thanks again!

---

