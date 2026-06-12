---
title: "Lan between linux and Dosemu"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by acu.tm on 2010-04-25
hi everyone. you know, I have a problem setting the lan between 2 pcs and using it with DOSemu. 
what I have to do is to run a program in DOS (written in Dbase) in both computers, using and editing the same databases. 
I searched all I could, and I'm nearly finishing all this. 
My problem now is :

In one computer I have DOSemu, and the folder which contains the program, and in the other computer, only the DOSemu. The easiest way to share the folder i read it was to share it in Ubuntu and do this: 

> Crear carpeta a montar en /mnt
> Sudo mkdir /mnt/carpetaLocal
> Montar carpeta
> Sudo Smbmount //servidor/carpetaCompartida /mnt/carpetaLocal
> Lanzar DOSEMU y escribir
> Lredir h: linux\fs/mnt/carpetaLocal 

but when i try to enter this order in DOSemu, I got an error, and I can't do this. 
So, what did I do ?. i tried to do this "Lredir h: linux\fs/mnt" instead of what is written there.  But when I enter drive H: in DOS , and i make DIR, i see that the folder "carpetaLocal" appears as a file, and not as a floder, so I cannot enter there :confused: . How could i solve this ? it's definitely killing me :lolflag:

thanks, and sory for my bad english

---

