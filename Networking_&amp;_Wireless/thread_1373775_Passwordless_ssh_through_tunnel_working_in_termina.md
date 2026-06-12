---
title: "Passwordless ssh through tunnel working in terminal but not used by KDE apps"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by tospo on 2010-01-06
I need to log in to a remote machine at work by setting up an ssh tunnel, so in my ssh config I have something like this:

```
Host TheWorkGateway
HostName some.IP.address.here
LocalForward SomeLocalPort TheWorkMachine:22

Host TheWorkMachine
HostName localhost
Port SomeLocalPort
```

Then I connect with this command:
```
ssh -N -f -q TheWorkGateway; ssh -X TheWorkMachine
```

and that's all working fine and I can access TheWorkMachine in Dolphin and work on files with Kate via sftp but I'm getting sick of having to enter my password for TheWorkMachine all the time.
I now set up a private/public key pair on my home machine and copied the public key to .ssh/authorized_keys2 on TheWorkMachine.
This works as expected when I run the above ssh command in a terminal - I get prompted for the password on the gateway machine but not the for the second one (TheWorkMachine) anymore. 
However, Dolphin and Kate still keep asking for my SFTP password - what am I doing wrong? SFTP is just using SSH right? Why is that different from using SSH on the command line? I suspect that it's something with my tunnel setup but I don't know what. Thanks for your help!

---

