---
title: "Networks connections are off!!!"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by christianikolai on 2009-09-01
Hi there...
I have  **ubuntu 9.04** in a notebook, with 2 networks connections (rj45 and wireless), when i begin to use wireless conecction, and i put tha password to access, a message appeared like "security ring" something like that.

I followed this tutorial [http://mundogeek.net/archivos/2007/08/31/como-hacer-que-el-gestor-de-claves-de-gnome-deje-de-preguntar-la-contrasena/](http://mundogeek.net/archivos/2007/08/31/como-hacer-que-el-gestor-de-claves-de-gnome-deje-de-preguntar-la-contrasena/) to eliminate this message, and when i write 

```
sudo aptitude install wicd
```
my network connections are off.
:confused:
ifconfig command return this:
```
lo    Link encap:Bucle local
      inet direccion:127.0.0.1 Mascara:255.0.0.0
      direccion inet6: ::1/128 Alcance: Anfiitrion
      ARRIBA LOOPBACK CORRIENDO MTU:16436 Metrica:1
      RX packets:128 errors:0 dropped:0 overruns:0 frame:0
      TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
      colisiones:0 txqueuelen:0
      RX bytes:10316 (10.3KB) tx bytes:10316 (10.3 KB)
```

/etc/networks/interfaces only says:
```
auto lo
iface lo inet loopback
```

I dont have the option en System>>Preferences>> Networks Connections

How can i recuperate mys networks connections?

Thanks for your help.

Best Regards

---

### Post by shredder12 on 2009-09-01
I can't open the link right now.. 
but i think your problem is disabling of your Gnome NetworkManager.
Actually wicd is a  network manager and when you installed have it might have disabled it..
so you can either try jst restarting gnome Network manager
```
sudo /etc/init.d/NetworkManager restart
```

afte executing it you should be able to see your network connctions..
if the problem persists then uninstall wicd..
Hope that helps..

---

### Post by christianikolai on 2009-09-01
Thanks for the answer **shredder12**,

I tried to restore with
```
sudo /etc/init.d/NetworkManager restart 
```
but any good result

I tried to install again wicd, downloading the tar.gz file, and i have not had any problem.

So when i reboot tha notebook, **all is ok** again, so now im working with wicd like network administrator.
:o

Best Regards

---

### Post by shredder12 on 2009-09-02
good 4 u.. :)
plz.. mark this thread solved by selecting the option in "thread tools"

---

