---
title: "Connect computer with Linux Mint to a Windows server via Internet"
date: 2022-11-14
forum: MINT
---

### Post by sarolmos on 2022-11-14
Hello! I need to connect my computer (Linux Mint) to a windows server via internet connection. How can it be done? Thanks in advance!

---

### Post by jeremy31 on 2022-11-14
Moved to Mint subforum

---

### Post by TheFu on 2022-11-14
> **sarolmos said:**
> Hello! I need to connect my computer (Linux Mint) to a windows server via internet connection. How can it be done? Thanks in advance!

Mint if moving farther and farther away from Ubuntu.  Best to ask this question in the Mint forums, which have lots of helpful people too.

However, the type of "internet connection" that is provided by the Windows server will determine what's possible.  I truly hope they don't allow file sharing over the internet via CIFS.  That would be a huge, huge, huge, security failure.  Even the seldom used CIFS encryption isn't consiered secure enough for use over the internet any more than Samba should be used.

Could you please be more specific as to what 
> connect my computer to a windows server via internet connection. 
means?  There are lots and lots of protocols used for different sorts of connections. A few can be used safely over the internet, but most cannot, which is the same for all computers. Not all network connections are safe for use over the internet.

---

### Post by MAFoElffen on 2022-11-15
For an shh connection from "anything" to a Windows Host, the Win Host needs to be Win 10 build 1909 or newer (That would also mean Windows Server 2019 or newer(1)...)
```

Add-WindowsCapability -Online -Name OpenSSH.Server*

```
Then install OpenSSH Server as a feature (through the GUI or Powershell). After installation the services are deafault off, so nee to be turned on as a service, set to autostart
```

Start-Service sshd

Set-Service -Name sshd -StartupType 'Automatic'

Start-Service &#8216;ssh-agent&#8217;

Set-Service -Name &#8216;ssh-agent&#8217; -StartupType 'Automatic'

```
And any other config changes such as ports, auth keys, etc. Then open a port through the firewall (adjust if you set a non-default port)
```

New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22

```
Notes:
1- OpenSSH Server can be installed on Windows Server 2016, but is "manually" downloaded and manually installed... outside of the normal MS channels.

---

