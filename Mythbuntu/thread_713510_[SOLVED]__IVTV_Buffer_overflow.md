---
title: "[SOLVED]  IVTV Buffer overflow"
date: 2008-03-02
forum: Mythbuntu
---

### Post by foxbuntu on 2008-03-02
There is a known issue that sometimes arises from IVTV Driver Based Capture Cards. The card will prodice buffer overflow messages in 'dmesg' and also stop recording. 

The fix for this issue has been to add:

```
vm.mem_free_kbytes=16384
```

into:

```
/etc/sysctl.conf
```

As of the coming up release of Mythbuntu-Control-Cetnre we have added this as a feature to the Advanced page. Simply click on the option if you are using and IVTV Based card and are experiencing problems, then apply the change.

A reboot will be required if applied while/after this error occurs.

---

