---
title: "SSH/SFTP connection problem on Hardy"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by pistik on 2008-12-22
Hi all,

i am running Hardy Heron and i have the following problem. I need to connect to a computer cluster, which i normally do via sftp through nautilus. Work fine from school, but not from home.

nautilus claim connection time out, a played around the sshd config but didn't help.

I can connect through Putty by ssh to the server, but if i try to run ssh from the console i am requested for my password and then i get:

Password: 
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 0
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

i also tried to connect using fish in konqueror, sftp in krusader (connection is broken error). None if it worked. I can connect my account from vista through WinSCP, running on the same machine. I would like to use sftp from ubuntu using some Gui to acess file more easily, ideally nautilus.

Any solutions/debugging ideas?

cheers pistik

---

