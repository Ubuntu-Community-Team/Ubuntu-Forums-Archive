---
title: "Wine error"
date: 2017-08-11
forum: Multimedia Software
---

### Post by steveredshaw on 2017-08-11
After installing Wine 2, I tried to run a windows program, but got the following errors in the terminal (I ran it from a terminal command because wine is not appearing in my menu or right-click pop-up window)

```
err:ntdll:RtlpWaitForCriticalSection section 0x7bd09680 "loader.c: loader_section" wait timed out in thread 001b, blocked by 001c, retrying (60 sec)err:ntdll:RtlpWaitForCriticalSection section 0x7bd09680 "loader.c: loader_section" wait timed out in thread 001a, blocked by 001c, retrying (60 sec)
steve@steve-ubuntu-studio ~ $ err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
err:seh:setup_exception_record stack overflow 848 bytes in thread 0034 eip 7facec0a esp 00240fe0 stack 0x240000-0x241000-0x340000

```

Do I need more dependencies or what....?

Thanks

---

### Post by Autodave on 2017-08-11
What program are you trying to install?  The Wine icon should be on the main screen you get when you click on the mouse in the top left corner. (Right under System.)

---

### Post by steveredshaw on 2017-08-16
I've tried an .exe and a .msi - they do not run - the issue is why, when I have installed Wine, does it not show up on a right-click window, or on the app menu or work in terminal? How can I overcome the errors?

---

