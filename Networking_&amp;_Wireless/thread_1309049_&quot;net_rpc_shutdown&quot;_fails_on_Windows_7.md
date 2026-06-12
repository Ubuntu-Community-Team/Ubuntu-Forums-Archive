---
title: "&quot;net rpc shutdown&quot; fails on Windows 7"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by Jarod42 on 2009-11-01
Hi,
I am trying to shutdown Windows 7 from my Ubuntu 9.10 server using the following command:```
net rpc shutdown -t 60 -f -C <some commment> -I <computer> -U <username> -d 1
```

This results in the following error message:> cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_ACCESS_DENIED received from host <computer>!
Shutdown of remote machine failed!
rpc command function failed! (NT code 0x00000005)
initshutdown pipe failed, trying winreg pipe
Could not initialise pipe \winreg. Error was NT_STATUS_OBJECT_NAME_NOT_FOUND

Turning off User Account Control (UAC) solves the problem, but is definitely not what I want.

Does anyone know how to shutdown Windows 7 remotely from a Linux machine without turning off UAC under Windows?

Regards.
 Jarod

---

### Post by Tee.Gee on 2009-12-15
Hi Andre,

did you ever work out how to do this?
I'd be interested in a solution that doesn't involve disabling UAC

Cheers,
  Tom

---

### Post by Jarod42 on 2009-12-21
Hi Tom,
I have not found a solution yet.

Jarod.

---

### Post by Tee.Gee on 2009-12-21
Let me know if you find one. This might also solve the problem that I'm having with remotely adding users to local groups on a domain machine.
If you switch off UAC, it's fine but that's really only the last resort.

Cheers,
  Tom

---

### Post by GrfyGrumpyBear on 2010-02-14
Hey, just to let you know I found a solution for this problem, just follow the steps listed here: [http://www.howtogeek.com/howto/windows-vista/enable-mapping-to-hostnamec-share-on-windows-vista/](http://www.howtogeek.com/howto/windows-vista/enable-mapping-to-hostnamec-share-on-windows-vista/)

Hope this helps!

---

### Post by Akim on 2010-06-02
I found the solution after many time trying (I HATE VISTA):

[http://www.howtogeek.com/howto/windows-vista/enable-mapping-to-hostnamec-share-on-windows-vista/](http://www.howtogeek.com/howto/windows-vista/enable-mapping-to-hostnamec-share-on-windows-vista/)

With adding this key the shutdown works fine :P

---

