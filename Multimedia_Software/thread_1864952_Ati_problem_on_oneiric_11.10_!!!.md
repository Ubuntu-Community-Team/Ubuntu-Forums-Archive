---
title: "Ati problem on oneiric 11.10 !!!"
date: 2011-10-19
forum: Multimedia Software
---

### Post by papampi on 2011-10-19
I have problem with my ati HD 4250 on oneiric 11.10
i tried this guide [ Installing Proprietary Drivers a.k.a. Catalyst/fglrx ]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide") also i tried swx11 from this post and i have plenty of problems !

payam@PAYAM-UBUNTU:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

here is what i done and shell output : 

[http://pastebin.com/sxhnFew2](http://pastebin.com/sxhnFew2)

any idea how to solve this ????

---

### Post by papampi on 2011-10-19
I tried to instal aditional driver !!
with same result 
```
payam@PAYAM-UBUNTU:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
payam@PAYAM-UBUNTU:~$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  22
  Current serial number in output stream:  22

```
still unity not work!!!

---

### Post by ubu_dynamite on 2011-10-19
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by papampi on 2011-10-19
> **ubu_dynamite said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Thnx mate !
I already done those steps more than 10 times !
And still get the same result

---

### Post by larsivi on 2011-10-24
I had the exact same problem, and posted my solution here:

[http://ubuntuforums.org/showthread.php?p=11387260#post11387260](http://ubuntuforums.org/showthread.php?p=11387260#post11387260)

---

