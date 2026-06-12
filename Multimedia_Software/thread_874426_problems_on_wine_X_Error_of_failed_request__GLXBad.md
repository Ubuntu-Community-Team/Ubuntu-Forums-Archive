---
title: "problems on wine X Error of failed request:  GLXBadContext"
date: 2008-07-29
forum: Multimedia Software
---

### Post by bambanx on 2008-07-29
Hi , (my english is bad :D ) i have a problem with some programs on wine with my drivers ati , but with mesa not problem , this error give me when excecute somes aplications :
gatito@gatito:~$ wine '/home/gatito/.wine/drive_c/Archivos de programa/e frontier/Poser 7/Poser.exe'
fixme:shell:DllCanUnloadNow stub

fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 30/03/2008, dlt (d/m/y): 12/10/2008
fixme:gdi:ExtCreatePen Hatches not implemented
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  22494
  Current serial number in output stream:  22494
wine: Unhandled page fault on read access to 0x00000200 at address 0xf7f5e09d (thread 0009), starting debugger...

my system is hardy heron 64 bits on dell inspiron 6400 with ati x1400 .

for any help thanks .

---

### Post by riki137 on 2011-08-17
Same here.
```
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13df00,0x13de48): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x9ef12c,0x00000000), stub!
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  3024
  Current serial number in output stream:  3024

```

---

