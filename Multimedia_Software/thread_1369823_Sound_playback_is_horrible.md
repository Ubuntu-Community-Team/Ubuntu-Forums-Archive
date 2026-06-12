---
title: "Sound playback is horrible?"
date: 2010-01-01
forum: Multimedia Software
---

### Post by Blacklightbulb on 2010-01-01
I don't know what I messed up this time but the sound playback is horrible. The sound card is installed properly. That I just verified. The drivers however are messed up I think causing the playback to play at a wrong speed.

Any help appreciated!

---

### Post by Blacklightbulb on 2010-01-01
/bump

---

### Post by chriswyatt on 2010-01-01
Make?  Model?  Version of Ubuntu?

You can find out what sound card is installed by typing 'lspci' in a terminal (assuming it's a PCI sound card).

---

### Post by JC Cheloven on 2010-01-01
If your card needs a proprietary driver, try reinstalling it, or using a different version. This should appear in system- administration- hardware controllers. 

Perhaps posting the output of lspci could help...

---

### Post by Blacklightbulb on 2010-01-02
I just reinstalled the card and done some random stuff. It's back to normal now! Thanks!

---

