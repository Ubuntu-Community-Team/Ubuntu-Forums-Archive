---
title: "lose connection to backend"
date: 2009-05-16
forum: Mythbuntu
---

### Post by relic2202 on 2009-05-16
Hi, 

i keep losing connection to the backend, and get the message connot connect to backend server, make sure ip address is correct and that mysql is running.

When i get that, i can connect to mysql on the command line, but the only way i can find to fix it is to reboot. It seems to be doing this quite a lot lately.

Any suggestions? Thank you.

---

### Post by ian dobson on 2009-05-17
Hi,

Can you provide abit more information:-

1) Frontend/Backend on the same system or different systems
2) What version are you running
3) Do yo see anything in the /var/log/mythtv/fronted or /var/log/mythtv/mythbackend.log files when you use the connection.

Regards
Ian Dobson

---

### Post by relic2202 on 2009-05-17
Hi Thanks for the reply.

> 1) Frontend/Backend on the same system or different systems
Frontend and backend are on the same machine.

> 2) What version are you running
8.10

> 3) Do yo see anything in the /var/log/mythtv/fronted or /var/log/mythtv/mythbackend.log  when you use the connection.

I found this in the frontend log, at the same time the backend log looked normal. A little more information that may be relevant. I had a recording set up that should have been about half way through when this happened, it never recorded. The errors in the frontend would have started at the same time that i switched on the tv to watch a  program.



```
2009-05-16 20:07:40.234 AFD: codec MP3 has 1 channels
2009-05-16 20:07:40.234 AFD: Opened codec 0x97788a0, id(MP3) type(Audio)
2009-05-16 20:07:40.234 AFD: Opened codec 0x98c3f40, id(DVB_SUBTITLE) type(Subtitle)
2009-05-16 20:39:35.004 [mpeg2video @ 0xb72ee764]ac-tex damaged at 36 2
2009-05-16 20:39:35.026 [mpeg2video @ 0xb72ee764]Warning MVs not available
2009-05-16 20:45:02.843 Connecting to backend server: 192.168.0.181:6543 (try 1 of 5)
2009-05-16 20:45:02.843 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the
                        proper IP address.
2009-05-16 20:45:02.906 Connecting to backend server: 192.168.0.181:6543 (try 1 of 5)
2009-05-16 20:45:02.906 Error: File 'myth://192.168.0.181:6543/1009_20090502220000.mpg' missing.
2009-05-16 20:45:02.907 Connecting to backend server: 192.168.0.181:6543 (try 1 of 5)
2009-05-16 20:45:02.907 Error: File 'myth://192.168.0.181:6543/1009_20090502220000.mpg' missing.
```
Regards
Ian Dobson[/QUOTE]

---

### Post by ian dobson on 2009-05-17
Hi,

If the backend and frontend are running on the same box why are you using the external IP address? Try using localhost for your sql server/frontend connection to your backend.

Regards
Ian Dobson

---

### Post by relic2202 on 2009-05-17
Hi,

> **ian dobson said:**
> Hi,

If the backend and frontend are running on the same box why are you using the external IP address? Try using localhost for your sql server/frontend connection to your backend.

The machine i am having the issue with is the only backend and also a frontend. I do also have 2 other machines that i sometimes use as a frontends, in the backend config app there are 2 places to enter ip addresses, the first says local backend: Enter the ip address of this machine (if there are any remote frontends use an external ip address, ie not 127.0.0.1), the second place is labeled ip address of remote backend, if this is the only backend should be the same as above.

If I enter anything other than 192.168.0.181 for either of the addresses then the main machine works, but none of the backends seem to be able to connect.

I think you may be on the right lines though, I know at some point last night i had network problems and had to reboot my router so they may be connected.

Is there anyway i can configure this so that the main machine doesn't go external but the other frontends still work?

Thanks,
Tony

---

