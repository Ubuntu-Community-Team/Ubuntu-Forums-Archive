---
title: "nautilus crashes after network transfer"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by mmoalem on 2010-02-28
hi there all - i move a file across my home network using nautilus (file is moved from ubuntu machine to windows xp machine) - when the transfer finishes nautilus crashes
launching nautilus from terminal gives me this:
> michel@ubuntu-laptop:~$ nautilus

(nautilus:2961): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-dropbox 0.6.1
Initializing nautilus-clamscan extension
Initializing nautilus-gdu extension

** (nautilus:2961): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2961): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2961): WARNING **: No marshaller for signature of signal 'ShareCreateError'


after transfer and crash the output is:
> sys:1: Warning: g_strsplit: assertion `string != NULL' failed
sys:1: Warning: g_strv_length: assertion `str_array != NULL' failed
Segmentation fault


file transfer works fine - the crash happens after first file transfer completed - sometimes after the second file start transfering - second file never finishes the transfer

using gnome-commander has no such problems

---

