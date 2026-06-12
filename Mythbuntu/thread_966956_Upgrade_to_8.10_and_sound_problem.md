---
title: "Upgrade to 8.10 and sound problem"
date: 2008-11-01
forum: Mythbuntu
---

### Post by raptorjr on 2008-11-01
In 8.04.1 i had sound. After upgrade to 8.10 i dont get any sound, in any player.
If i run the 8.10 LiveCD i get sound. So it must be some config file or something that is messing with me.
What files do i need to copy from the LiveCD to get the sound working again?
Or is there any way to reinstall everything that is handling the sound?

---

### Post by raptorjr on 2008-11-02
I  must say, a very logical solution to my problem. Downgrade the NVidia driver from 177 to 173 and i got my sound back :confused:

Would this be considered a bug?

---

### Post by ghuber on 2008-11-02
I had video problems and used Envy to reinstall the nvidia drivers.  Envy listed 173 as supported with my card but not 177.  177 was installed by the upgrade.

---

### Post by enrique.lopez on 2008-11-02
I have sound problem in diskless client it's very slow.

---

### Post by Madox.Net on 2008-11-03
Confirm the same problem with the nvidia 177 driver.  Reverting to 173 fixed it.

---

### Post by agamotto on 2008-11-03
I am using the 177 drivers, and noticed that I had to drop to XFCE, go into Sound, and add Master to the PCM control shown.  With this, both the PCM and Master can be raised to 100% if needed, which solved the problem for me.

---

### Post by raptorjr on 2008-11-03
> **agamotto said:**
> I am using the 177 drivers, and noticed that I had to drop to XFCE, go into Sound, and add Master to the PCM control shown.  With this, both the PCM and Master can be raised to 100% if needed, which solved the problem for me.

I dont really understand what you did. Could you explain a little more for a linux noob what i should do =)

---

