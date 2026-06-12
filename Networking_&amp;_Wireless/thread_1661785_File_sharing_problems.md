---
title: "File sharing problems"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by devsen on 2011-01-07
Hi,

Having installed samba4 and smbfs I am trying to share my documents directory into my home network. But when try to do this I get the following error -

Samba's testparm returned error 1: Traceback (most recent call last):
  File "/usr/bin/testparm", line 43, in <module>
    import samba
  File "/usr/lib/python2.6/dist-packages/samba/__init__.py", line 45, in <module>
    from samba._ldb import Ldb as _Ldb
ImportError: /usr/lib/libgensec.so.0: undefined symbol: _dcerpc_binding_handle_data

I am using 10.10

Please help I do need to do this as I want to use ubuntu machine as my backup.

Thanks

---

### Post by Morbius1 on 2011-01-07
Any reason you installed Samba4:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production. In particular, no guarantees are made with regard to upgrades between versions.
In fact the package name itself is something like "4.0.0~alpha9". Unless you're a samba tester I'd remove it and reinstall the default samba.

---

### Post by devsen on 2011-01-07
Thanks for that. When I tried the command sudo samba restart, I got the message samba is not installed - install samba by sudo apt-get install samba4 - thats the reason I did that. I will uninstall samba4 and hope this solves the problem.

Thanks again for your reply.

---

### Post by Bucky Ball on 2011-01-07
Are the machines you are trying to network with Ubuntu also?

---

### Post by endotherm on 2011-01-07
well, to restart samba you should use the 'service' command, and sambas service is called 'smbd'
```

sudo service smbd restart

```

as for testparm, it is a diagnostic utility for samba configs. you can run it like this:
```
sudo testparm -s
``` and it shoudl point out any configuration errors you may have made. 
try running testparm and let us know what it spits out. 

as for Morbius' advice, I'd take it. ubuntu and samba4 are not quite ready to work together.

---

### Post by sachin0000 on 2011-07-13
Hi, as I was getting the same error posted above... So I too removed 'samba4' (which I had installed earlier) & reinstalled 'samba'. Later I ran "sudo testparm -s", which gave me following message.. 
> [B]Traceback (most recent call last):
  File "/usr/bin/testparm", line 43, in <module>
    import samba
  File "/usr/lib/python2.6/dist-packages/samba/__init__.py", line 45, in <module>
    from samba._ldb import Ldb as _Ldb
ImportError: /usr/lib/libgensec.so.0: undefined symbol: _dcerpc_binding_handle_data[/B]

so please help me further in this...as I am quite new to linux...

-Thank you.

---

### Post by Bucky Ball on 2011-07-13
sachin, please start your own thread with a suitable title. It becomes confusing trying to assist two OPs in the same thread. 

You are more likely to get better and more specific help with your problem by doing this. ;)

---

