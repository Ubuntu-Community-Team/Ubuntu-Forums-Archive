---
title: "anyone help me to install this file"
date: 2009-03-14
forum: Multimedia Software
---

### Post by toblina63 on 2009-03-14
i download my camera driver file and it named :

sn9c1xx-1.48.tar.gz

and this the files in it :

[IMG]http://img12.imageshack.us/img12/4786/43976526.png[/IMG]

i need to install this camera driver but i didn't know how to do it 


anyone know how ?????? ;);)

---

### Post by albandy on 2009-03-14
First you need to unpack it:

go to console and type:

cd the_folder_where_I_downloaded_the_driver
tar zxvf sn9c1xx-1.48.tar.gz
cd sn9c1xx-1.48

now read the file sn9c102.txt

usually in this kind of files you should do the commands
make
make install

but ensure you have all requirements installed, specified in the sn9c102.txt file.

---

### Post by binbash on 2009-03-14
you are not gonna do ./configure, you will do make and sudo make install.But check the deps as mentioned above

---

