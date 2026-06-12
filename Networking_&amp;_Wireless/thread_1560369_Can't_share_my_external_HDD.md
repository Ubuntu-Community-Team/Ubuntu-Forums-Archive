---
title: "Can't share my external HDD???"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by JD32 on 2010-08-24
Im running Ubuntu 10 desktop. Im trying to make it my fileserver for my windows laptops. The computer im using only has a 40GB HDD so I want to be able to share my 1TB external HDD. I cant get it to work to save my life. I read another forum from a guy trying to do something similar but it still wont work.

I reformatted the drive to ext4, added it to fstab and gave it 777 permission but windows still keeps giving me an error thats saying there might be a problem with my spelling or a problem with my network?

Any help would be greatly appreciated!

---

### Post by dtoronto on 2010-08-24
Maybe I'm not understanding correctly, but if you're trying to use an ext4 hdd and share to a windows computer the formatting is incompatible.  You'll probably need to get a samba server set up on your linux box to be able to share hdd with a windows cpu.  If I am incorrect in understanding your setup please let me know.

---

### Post by JD32 on 2010-08-24
I have samba installed, i can access files on the boxes internal HDD on my windows computer, i just cant access my external HDD through the box... I don't no if ext4 is even what i need or anything. I'm real lost haha

---

### Post by vlamnire on 2010-08-24
So your problem is you cannot access the files with the Ubuntu PC but you can over the network with Windows?

---

### Post by JD32 on 2010-08-24
opposite, Can access files on the ubuntu computer but can't through windows. I can see the file but when i try to open it windows give me a error message that the file does not exist and the spelling might be wrong (and its not wrong)

---

