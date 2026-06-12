---
title: "[Nvidia] Has anyone successfully been able to get..."
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by theanswriz42 on 2006-06-23
...The Nvidia GeForece 4 420 Go chipset working with the nvidia drivers? I've been having problems since Dapper Drake flight 6 and still haven't been able to get anything worked out.

Cheers

---

### Post by theanswriz42 on 2006-06-24
ttt

---

### Post by K.Mandla on 2006-06-25
I have a GeForce4 440 and I usually just *apt-get install nvidia-glx-legacy*. I get full 3D rendering at native resolution. Does that help you at all?

---

### Post by tseliot on 2006-06-25
See point 7 of the Problems section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

P.S. you can use the latest driver

---

### Post by theanswriz42 on 2006-06-26
[QUOTE=tseliot]See point 7 of the Problems section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

P.S. you can use the latest driver[/QUOTE]

Thanks! These updated drivers/instructions work like a charm.

Cheers

---

### Post by theanswriz42 on 2006-06-26
[QUOTE=K.Mandla]I have a GeForce4 440 and I usually just *apt-get install nvidia-glx-legacy*. I get full 3D rendering at native resolution. Does that help you at all?[/QUOTE]

No, the problem I was having was that there was the vertical line on the right hand side of the screen (it was really just because the driver changed resolutions and I couldn't change it back). Everything works well now. 

Cheers

---

