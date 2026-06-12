---
title: "Proxychains not work"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by _Matt_ on 2010-11-24
Hi everybody

i'm connected to internet from university dial-up that is through an HTTP proxy server ( Squid 2.7 STABLE3 )

Other people using windows and a program called proxifier can play to online game forcing the connection through the proxy.
I'm using Ubuntu Maverick 10.10 and i want to play poker online.
I have correctly installed poker client and to force connection i could use Proxychains.

I have configured the file /etc/proxychains.conf adding the proxy ip, post, user and password as wrote in the TAG.
In the shell i give the command: proxychains wine C:\\Programmi\\Full\ Tilt\ Poker\\FullTiltPoker.exe 

and the program doesn't work.

this is what it write in the shell:
```
ProxyChains-3.1 (http://proxychains.sf.net)
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:CoGetClassObject class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:create_server class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:CoGetClassObject no class object {6e4fcb12-510a-4d40-9304-1da10ae9147c} could be created for context 0x7
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:win:FlashWindowEx 0x32be9c
|R-chain|-<>-10.250.70.250:3128-<><>-91.211.96.7:443-<><>-OK
|R-chain|-<>-10.250.70.250:3128-<><>-91.211.96.7:443-<><>-OK
|R-chain|-<>-10.250.70.250:3128-<><>-91.211.96.7:443-<><>-OK
|R-chain|-<>-10.250.70.250:3128-<><>-91.211.96.7:443-<><>-OK
|R-chain|-<>-10.250.70.250:3128-<><>-91.211.96.7:443-<><>-OK
|R-chain|-<>-10.250.70.250:3128-<><>-91.211.96.7:443-<><>-OK
fixme:font:WineEngRemoveFontResourceEx (L"C:/Programmi/Full Tilt Poker/./Fonts/Univers-CondensedBold.otf", 10, (nil)): stub
```

sorry for my bad english...

---

