---
title: "Unable to get SSH Agent Forwarding working"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by boyracerr on 2009-05-31
I recently installed Ubuntu 9.04 (using a VMWare Player image). I can successfully ssh in from the host XP installation using Putty, with passwordless authentication supplied by Pageant

However, despite having:

- set the Putty configuration to allow agent forwarding
- added the following entry in /home/user/.ssh/config:

Host localhost
User user
ForwardAgent yes

I cannot successfully get the agent to forward when using:

ssh -vvv localhost (I'm just using localhost as test, this has failed with other servers as well)

Looking at the debug output, it seems all goes well until this point:

debug3: no such identity: /home/user/.ssh/id_dsa

and then it fails and drops back to password identification. I cannot find anything helpful regarding this error message and problem. Anybody have any ideas please?

Thanks in advance,

---

### Post by Brandon Williams on 2009-05-31
Just to be sure I understand the problem, you ssh from XP into the hosted vmware linux install using the 'forward ssh agent' option, and then you want to be able to connect from linux into another system using the keys from the XP ssh agent, right?

The first thing to do is verify that your ssh agent is actually being forwarded. After connecting to linux, run 'ssh-add -l' to list all the keys loaded in your current agent. If you have not correctly forwarded your agent from XP, the output will be 'Could not open a connection to your authentication agent.' If you have correctly forwarded your agent, you will get a list of the keys loaded in the agent.

If the agent is being correctly forwarded, the next thing to consider is the ssh version. What kind of key are you using? RSA, DSA, or RSA1? If it's RSA1, then you are using SSHv1. The default on Ubuntu will be SSHv2. You may have to explicitly specify SSHv1 as the protocol using the -1 flag. This probably isn't it, but it's worth double-checking.

If you still don't have an answer after double-checking those two things, it may be worth running the ssh daemon in debug mode in order to get a better idea of what's happening. Stop sshd in your linux instance, and then run it from the command line with '-eddd' as one of the command line flags. This will make it run in verbose debug mode and send its output to the screen instead of the log.

PS: Just in case it wasn't clear, the 'ForwardAgent' setting in /home/user/.ssh/config impacts whether the agent on linux will be forwarded to the next machine you ssh to. If the agent hasn't been correctly forward to linux, then the 'Forward Agent' setting in the linux user config with have no impact.

---

### Post by boyracerr on 2009-05-31
Thanks for your quick response,

Yes, you restated correctly, other than that I am not using ssh itself but rather the PuTTy emulator for Windows. However, I have tried from my MacBook using ssh with the same result. This suggests to me the problem is with the Linux machine.

Running ssh-add -l gives 'the agent has no identities', so as you say I guess the agent is not forwarded correctly. However, I have tried to eliminate this as an error at the client end:

- I duplicated my saved settings for a server which successfully forwards, changing only IP and username. Same results.
- I tried using a more 'native' ssh on my MacBook as described above; again, works on one server but not this one.

Regarding the key type used, its DSA I think - I've used it for some time on RedHat and Debian servers without problems. Note that I can ssh into the Ubuntu machine without a password; I am unable to go on to another machine however.

Oh I should say that it took me a little time to get the password authenticate working; it may therefore be possible that I messed up config or permissions in some way, but there is little I can see.

Restarting the ssh service in debug mode... well I see a lot of things, but nothing regarding forwarding. Anything in particular I should look for?

Oh, this might or might not be relevant, but the agent sockets (/tmp/ssh-randomletters/agent.processID) are being created on login every time.

Thanks!

---

### Post by boyracerr on 2009-05-31
If I create a new user, agent forwarding works perfectly without any changes. So, this suggests that I managed to mess something up somewhere along the line.

Sorry to have wasted your time - I am happy to use the new user.

However, if anybody would like to solve the problem out of interest, I would be happy to know what I did for wrong for future reference.

---

### Post by Brandon Williams on 2009-06-01
My guess is that you're doing something in your login environment (.profile, .bash_profile, .bash_login, or .bashrc) that is resulting in the necessary environment variables being over-written. There should be an SSH_AUTH_SOCK variable defined in your environment as a result of agent forwarding. If that is getting lost or over-written by something in your login environment, then you will not have access to the agent.

---

### Post by boyracerr on 2009-06-01
Correct; what I had done in my previous attempts to get authentication working was add these lines to the bottom of .profile:

eval `ssh-agent -s`
eval `ssh-add`

I thought these were correct, but apparently they conflicted in some way with Ubuntu's natural way.

Thanks again,

---

