---
title: "Want to install Mythbuntu without XFS partition"
date: 2010-05-02
forum: Mythbuntu
---

### Post by orduek on 2010-05-02
Hi,
After what seems to be a HDD failure I want to do a new installation of Mythbuntu on another Hard drive.
I alreadt have many TVshows there so I don't want to delete it.
I actually wondered what do I have to do in order to make only the root partition installation of Mythbuntu (without the XFS partition their making during installation).

the HDD has 1TB.
I want to partition approximately 20gb to the Mythtv /root (/home) partition and I want the rest to be unharmed.

how can I do that?
thank you very much.

---

### Post by tgm4883 on 2010-05-02
Mythbuntu doesn't use XFS anymore, it's EXT4 (and by default, one large partition).

What you would want to do though is during installation do custom partitioning. Then you can select which partitions get created and formatted.

---

