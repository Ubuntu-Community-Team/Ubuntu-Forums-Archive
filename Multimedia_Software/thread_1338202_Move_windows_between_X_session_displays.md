---
title: "Move windows between X session displays?"
date: 2009-11-26
forum: Multimedia Software
---

### Post by bheyes on 2009-11-26
Hello all,

Does anyone know how to move active windows between X session displays?

Thanks,

-Brent

---

### Post by ilil on 2009-11-26
Right mouse click on window title and choose "Move to ..."?

---

### Post by bheyes on 2009-11-26
That moves the window to another workspace, not another x session display.

---

### Post by ilil on 2009-11-26
Well, I think it is not possible to move to another session. As far as I know GTK toolkit caches such X things, so anyway you get segfaults...

---

### Post by Grenage on 2009-11-26
It's a completely different projection, so I don't think you can.

---

### Post by markbuntu on 2009-11-26
You would need to disable randr and use xinerama instead. AFAIK, this can only be done with the proprietary nvidia and ati drivers at the moment since xinerama has been deprecated and that functionality has not been implemented in randr yet.

If you are using the nvidia or fglrx (ati) proprietary driver you can do this from their control APIs.

---

