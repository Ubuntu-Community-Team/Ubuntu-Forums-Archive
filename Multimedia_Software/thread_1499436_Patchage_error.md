---
title: "Patchage error"
date: 2010-06-01
forum: Multimedia Software
---

### Post by Komputor on 2010-06-01
Well, now that I have Jack installed correctly I would like to see about setting up the patches, but when I start Patchage, I get this:

<output omitted>-laptop:~$ patchage
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Failed to connect to LASH.  Session management will not occur.
Loading configuration file ...~/.patchagerc
Unable to load file ...~/.patchagerc!
Connecting to Jack... could not connect to jack server.
terminate called without an active exception
Aborted
<output omitted>-laptop:~$ 
<end script>

So just wondering if I need to have Jack started *before* I open Patchage, or what else I may need to reconfigure.  Thanks again for all the help in advance!
:guitar:

---

### Post by cchhrriiss121212 on 2010-06-02
You need jack started before doing anything, and you can set it to run as an applet in the top right corner by checking a box in the setup window.

---

