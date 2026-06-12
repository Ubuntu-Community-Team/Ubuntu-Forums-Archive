---
title: "Flash just will ... not ... work!"
date: 2010-06-02
forum: Multimedia Software
---

### Post by agentchange on 2010-06-02
I have tried everything.  Synaptic, apt-get, installing from source every which way that is imaginable (unless, of course, my new kind of old computer is 64 bit and nobody told me), I've tried purging all of the old files and starting all over again, Flash-aid, Carly's Adobe tools.  It just does not make sense and I know (maybe?) that it is just some little little-known unmet dependency or setting or something.

I'm running Mythbuntu 10.04 backend/frontend on a P4 underclocked at 2 Ghz with 1 GB of RAM.  I just bought this new Azrock motherboard with the Intel GMA setup of HD audio and some 3D support (915GL Northbridge) but it has never mentioned that it was 64 bit. 

But wait a minute, I'm getting way off-track here, right?  I should be able to run the 32-bit version on any system, right?  So, I'm kind of stuck for the moment.  Any ideas?

---

### Post by agentchange on 2010-06-02
Oh yeah.  Whenever I try to play flash content, no matter what installation method I have used, it just prompts me to install it again, does not even recognize it.

---

### Post by gandaran on 2010-06-02
> But wait a minute, I'm getting way off-track here, right? I should be able to run the 32-bit version on any system, right? So, I'm kind of stuck for the moment. Any ideas?
yes, you can run 32-bits Ubuntu on your 64-bits hardware,
to find out what version of Ubuntu you have type in terminal
> uname -a
if you running 64-bits Ubuntu system its recommended you use 64-bits flash, you can also use 32-bits flash but you have to install it from apt-get or synaptic package manager, it wont work if installed in any other manner.

---

### Post by garvinrick4 on 2010-06-02
```
sudo apt-get install flashplugin-installer
```

Been running 64 bit Ubuntu for a while and no problems.

---

### Post by lovinglinux on 2010-06-02
> **agentchange said:**
> Oh yeah.  Whenever I try to play flash content, no matter what installation method I have used, it just prompts me to install it again, does not even recognize it.

That's weird, because FLASH-AID or Adobe Tools should have fixed that.

This usually happens when you have swfdec installed.

Are you using the default Firefox installation or some newer version installed manually?

Please post the output of these commands:

```
locate libflashplayer.so
```

```
locate firefox
```

---

### Post by dorothykinder on 2010-06-02
Was stuck with a similar kind of a problem.. me have too to check with my Linux..

---

### Post by agentchange on 2010-06-02
> **lovinglinux said:**
> That's weird, because FLASH-AID or Adobe Tools should have fixed that.

This usually happens when you have swfdec installed.

Are you using the default Firefox installation or some newer version installed manually?

Please post the output of these commands:

```
locate libflashplayer.so
```

```
locate firefox
```

At one point, I tried swfdec and that actually worked for at least one application, but have since reinstalled.  I do still have some lib files for that which I have now deleted.   I just installed again with Adobe Tools.  Here is the output.  The second one seems kind of peculiar.  The content in the top half of the output will not show me the beginning of the list, where my command should be.  Thank you for your help.

> justin@justin-desktop:~$  locate libflashplayer.so
/home/justin/libflashplayer.so
/home/justin/Desktop/libflashplayer.so
justin@justin-desktop:~$ 


> /home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2652AD2Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2694598Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/26F0B49Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/27160EDAd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/277F3B88d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/278D44D4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/27D6CA6Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/27DEE12Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/28416AC9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/287E0BD4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2913BD8Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/293F675Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/29D0B4BCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2A472870d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2A8C978Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2B51C902d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2B6F5CC1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2C820050d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2CEBB4DBd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2DB5B99Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2E333998d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2E396612d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2E968E86d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2EDF7773d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2EF8E4F3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2F58A3E5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2F789150d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/2F8EBA55d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3053BAF2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/31010742d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3163BE7Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3174E287d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/32CBC01Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/32D8CC0Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/32E4D1F2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3312DD87d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3401F677d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/342B59D4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3510C10Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/354CCC4Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3597A6B7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/35CBC67Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/35DD357Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3656895Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3680E218d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/36BCAC31d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/36E0E9C6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3781E27Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/37962085d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3808167Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3825AF1Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/384EAA57d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/388FD581d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/38B7E2CFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/38E81EE7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/39117741d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/39A08FB4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/39A9EFAFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/39B6D0D3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/39E36398d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3A04AFE6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3A38121Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3A921CB0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3AB97DA4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3B10472Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3B7460DBd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3B8260E9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3BCFD8E0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3CA3423Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3CF3DB7Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3D039AA4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3D733801d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3D7EF40Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3DABF9E5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3F29B3E7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/3FEE7AD7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/41082C74d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4144F81Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4154005Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/417D9389d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/41C46A5Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/42BC89D2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/42E81C02d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/43DC18BFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/43F6A3CEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/43FD7D88d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/447BA071d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/448CFDB9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4517ACAEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/46742FB6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/47A202A5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/47A7F1E2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/48A4DF75d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/48AB5148d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4A1F785Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4A4B0218d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4BA56AEDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4D149910d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4E077223d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4E0814E8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4E506655d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4E5F7F40d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/4FC35D7Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/50527471d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/50864DEBd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/50BCA682d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/50C4552Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/513BEEC3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/517282A1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/51AA27C0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5355A9A9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/539E1210d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5511F28Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5557914Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/55C4E2DFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/56479DAEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/574B598Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5765B547d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/57FF0005d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5957E06Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/597A7E7Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/59A744C3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5C1F6D4Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5C3BAE57d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5C52132Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5DE5E340d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5E20C036d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5F472896d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5FC96C73d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/5FEE7D64d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/603FA0DFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/60599C35d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/607104CCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/61237ECEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/61C576C6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/61CEC9CDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/626F07F7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/62A8E3F2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/63F8FBF5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6404101Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/644220B3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6464AB75d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/64B7F36Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/64D0F97Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/651D440Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/65A5F622d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/65A984BCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/65F155EFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6612A21Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/661CF5ABd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6655F2BCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/670090CFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/67312B36d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/67425CD6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/67D760A6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6828A452d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6836F601d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/688C50A2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/68E2D9A0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/68EA9B34d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/69081859d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6955720Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6A7E0D2Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6AE6D265d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6AE91B42d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6AF73031d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6AFF8905d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6B089E30d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6B9FBA41d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6BEE64CEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6C3989C7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6C639B9Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6D9B6121d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6DD04606d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6E21D3B4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6E351FC1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6E37AAD9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6F15DAB9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/6FD19286d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7091C87Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/70BB0369d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7151E991d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/71AB6649d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/71B1A4FCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/72765781d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/72EE3F6Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/72FE703Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/731C9A18d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/744F7BA9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/745BE006d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/74BA0415d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/74E2BE82d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/756BE370d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/75A65193d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/75DFEE33d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/75EAF4E2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7670903Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/76800A1Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/76A36466d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/778FF54Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/781C7638d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/78450B75d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/788D4EBEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/78BE0042d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/78DD6AD5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/793AE164d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7970D915d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7974BBE3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7996FE20d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/79CB3DB7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/79F1155Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7A0501BCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7A4ACF1Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7A96B218d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7AA3C0D8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7AC3A8B7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7B770DB1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7BC68B33d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7C300539d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7C4F1CD8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7D0DDE6Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7D437EBAd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7DC1E495d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7DD76C90d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7E10F0FBd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/7EF08D3Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8126B6D6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/822B6F54d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/82340EF1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/83468877d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8528B4BBd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/857DA20Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/859613D1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/86A26626d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/86BC71D0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/86BE6716d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8715C0B6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8723B4FDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/87350F95d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8785E996d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/87D832BEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/88984A3Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/891C120Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/89452699d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/89706651d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8A5B7717d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8B5ECCE6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8C55A6FDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8CCB3E1Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8CE38ECDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8CE5B5E5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8CF3B9F5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8E5FB63Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8E6CF6CDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8E7FA267d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8ED47703d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8EF671E5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8F272CD8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8F2792CDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8F6E20DDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8FDE01AEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8FE70B9Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/8FFEC886d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9015762Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/906F88B4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/90827B8Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/916295F5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/916C6A19d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/91770E4Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/91841375d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/92267A52d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/92C03CC1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/92D43BBCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/938ABF60d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/93DCEEA5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9409F4CCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/947B3B8Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/94862D8Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/94FD092Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/95C1C4F8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9611F10Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/96539F65d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9687D85Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/96F07FF3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/97B1402Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/97D08EC9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9854862Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/985D9A90d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/986CB8A7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/991FA64Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/992B48C1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/995F0267d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/997C7FAFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/99C70098d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9A162121d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9B03022Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9B873111d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9BB299BDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9BB9E28Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9BBDC223d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9C2E54D3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9C961468d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9D6979C3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9E4D90ACd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9F62E537d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/9FC83DF0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A027D5B9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A0528C71d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A087E7B0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A13081FFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A13DCB21d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A1A9B140d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A2B8C0CFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A3486CDBd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A34D4A3Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A3642A06d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A3887D31d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A38DFF6Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A4509DC6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A467B8A0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A520DCD7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A56E1DA7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A58C0C8Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A5D5DBDDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A5DCDBD5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A5EE2834d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A63CBB27d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A8D0A259d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A9452AE7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/A9592FCCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AAE7E5A7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AB56B39Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/ABEDC614d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AC2B485Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AC2E3845d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AC87BF95d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AC8CFD14d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AC9302FEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/ACD75E31d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AD2A13DCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AD71BD2Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/ADC764C3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AE8D9525d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AF44E6D3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AFDCE5EEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/AFED608Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B0180050d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B09E9807d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B1A74BD1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B1BCE912d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B1D24D4Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B2583B05d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B280DCB4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B30C8B46d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B4738509d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B5F98813d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B68BF5D3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B6B02019d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B6F22F21d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B7BE6869d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B7CD8AF8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B852E935d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B9296C54d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B92A9B3Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B9543197d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B96D3190d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B980895Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B9F80353d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/B9FEDCC6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BA491F70d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BA58E762d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BAA37C15d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BAB26EF8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BAC77A4Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BAFBBE9Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BBD03F7Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BC5F0076d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BD765568d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BDAA1963d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BECC5BB2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BF3B875Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BFC84E8Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/BFEA1B07d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C0041485d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C047D2A5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C082EB62d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C0EF9413d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C0F8FD14d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C17A025Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C1A90E34d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C2E73A0Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C3D6079Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C3E13780d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C42AE2C9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C4522735d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C4AD8829d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C548B36Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C57EADDAd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C58ED0E3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C5F22D30d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C631AEA9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C74979EEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C80617D1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C87A5F92d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C8B84D0Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C91E821Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/C98CFB44d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CA67FE10d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CA811AE9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CA976246d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CC0F50BAd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CC158DD6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CC244FA4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CD0BBD44d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CDD5CB75d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CE19E626d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CE6E2E3Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/CE9FEDC4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D00401A6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D06E73C8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D1252B6Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D17FD5E3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D1EBAD31d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D1FEAA03d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D24C2A8Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D254B9A0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D35F110Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D3D73F78d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D411F79Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D436855Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D46EFEF1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D55878FCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D5F8663Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D6631B86d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D792B1EDd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D82EE7E0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D968D6D9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D9E286FBd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/D9EBEFC1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DA544B4Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DA8625F6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DA87ACC9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DAD2D751d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DB880E9Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DB997E07d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DBBA02FEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DBC61C8Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DBFD1659d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DC64A14Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DC7518F7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DD280E04d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DD51E6AEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DD659897d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DE638BA4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DEA4974Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DF1BF7B4d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/DFAD3D66d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E0968DA2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E0EA6CA1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E0F503DAd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E1B11328d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E1EE372Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E273A149d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E288167Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E2A7063Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E39BA2ACd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E3A00B82d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E4202DD2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E5FB10D8d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E610CD7Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E69DAEB3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E6AC3D6Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E6E4DCDEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E6F8DFD6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E793BA55d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E7C731ECd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E7DF5D8Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E873F0CBd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E8C4D2A1d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E9A3684Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/E9AAFF16d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EB8DFFFFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EBCC1A4Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EC15C610d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EC1FE172d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/ECD41306d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EDA9AAC2d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EDDBA14Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EF1E9B6Cd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EFF1A085d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/EFF419D7d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F001DAACd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F05AC402d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F0FEDF75d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F23FAAA3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F334033Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F3676C2Dd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F3C78312d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F3DF6A61d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F4676182d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F55EF68Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F5BCEBFCd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F623C5D5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F625987Fd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F7B3F31Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F7B964ADd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F8234A71d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F85B3CA3d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/F8F6DDFEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FB0BC12Bd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FB539ED0d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FB606873d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FBBABBFFd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FC35BA35d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FCC8142Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FD2563CEd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FD3976D5d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FD75A284d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FE481DACd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FE7F9F7Ed01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FF442EBAd01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FF4C8827d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FF5640D9d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FFC61AF6d01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/FFFD926Ad01
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/_CACHE_001_
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/_CACHE_002_
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/_CACHE_003_
/home/justin/.mozilla/firefox/ytyb7ws0.default/Cache/_CACHE_MAP_
/home/justin/.mozilla/firefox/ytyb7ws0.default/FVD Single/supported_sites.txt
/home/justin/.mozilla/firefox/ytyb7ws0.default/OfflineCache/index.sqlite
/home/justin/.mozilla/firefox/ytyb7ws0.default/bookmarkbackups/bookmarks-2010-05-30.json
/home/justin/.mozilla/firefox/ytyb7ws0.default/bookmarkbackups/bookmarks-2010-06-01.json
/home/justin/.mozilla/firefox/ytyb7ws0.default/bookmarkbackups/bookmarks-2010-06-02.json
/home/justin/.mozilla/firefox/ytyb7ws0.default/chrome/userChrome-example.css
/home/justin/.mozilla/firefox/ytyb7ws0.default/chrome/userContent-example.css
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{6D1D11DB-3C6C-4db8-96E4-20F4A1088AAC}
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{888d99e7-e8b5-46a3-851e-1ec45da1e644}
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{c45c406e-ab73-11d8-be73-000a95be3b12}
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome.manifest
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/components
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/defaults
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/install.rdf
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content/fvd_download.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content/fvd_download.xul
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content/fvd_license.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content/fvd_license.xul
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content/fvd_settings.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content/fvd_settings.xul
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content/fvd_single.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/content/fvd_single.xul
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.download.dtd
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.download.properties
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.dtd
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.license.adult.txt
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.license.dtd
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.license.properties
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.license.usage.txt
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.properties
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.settings.dtd
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/locale/en-US/fvd.single.settings.properties
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.css
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.download.css
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.download.png
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.icon.png
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.license.css
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.main_button.large.png
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.main_button.small.png
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.notify.unsupported.png
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.search_button.small.png
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.settings.css
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/chrome/skin/fvd.single.settings.png
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/components/fvd_single_site_detector.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/components/fvd_single_site_detector.xpt
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/defaults/preferences
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/artur.dubovoy@gmail.com/defaults/preferences/fvd_single_setup.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{6D1D11DB-3C6C-4db8-96E4-20F4A1088AAC}/chrome.manifest
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{6D1D11DB-3C6C-4db8-96E4-20F4A1088AAC}/content
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{6D1D11DB-3C6C-4db8-96E4-20F4A1088AAC}/install.rdf
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{6D1D11DB-3C6C-4db8-96E4-20F4A1088AAC}/content/firefoxOverlay.xul
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{6D1D11DB-3C6C-4db8-96E4-20F4A1088AAC}/content/showmyip.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/.autoreg
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/GPL.txt
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/META-INF
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/NoScript_License.txt
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/chrome
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/chrome.manifest
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/components
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/defaults
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/install.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/install.rdf
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/mozilla.cfg
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/META-INF/manifest.mf
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/META-INF/zigbert.rsa
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/META-INF/zigbert.sf
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/chrome/noscript.jar
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/components/noscriptService.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/defaults/preferences
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{73a6fe31-595d-460b-a920-fcc0f8843232}/defaults/preferences/noscript.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{888d99e7-e8b5-46a3-851e-1ec45da1e644}/chrome
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{888d99e7-e8b5-46a3-851e-1ec45da1e644}/chrome.manifest
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{888d99e7-e8b5-46a3-851e-1ec45da1e644}/install.rdf
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{888d99e7-e8b5-46a3-851e-1ec45da1e644}/chrome/reloadevery.jar
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{c45c406e-ab73-11d8-be73-000a95be3b12}/chrome
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{c45c406e-ab73-11d8-be73-000a95be3b12}/chrome.manifest
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{c45c406e-ab73-11d8-be73-000a95be3b12}/install.js
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{c45c406e-ab73-11d8-be73-000a95be3b12}/install.rdf
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{c45c406e-ab73-11d8-be73-000a95be3b12}/license.txt
/home/justin/.mozilla/firefox/ytyb7ws0.default/extensions/{c45c406e-ab73-11d8-be73-000a95be3b12}/chrome/webdeveloper.jar
/usr/bin/firefox
/usr/lib/firefox
/usr/lib/firefox-3.6.3
/usr/lib/firefox-addons
/usr/lib/mozilla-firefox
/usr/lib/firefox/plugins
/usr/lib/firefox/plugins/gecko-mediaplayer-dvx.so
/usr/lib/firefox/plugins/gecko-mediaplayer-qt.so
/usr/lib/firefox/plugins/gecko-mediaplayer-rm.so
/usr/lib/firefox/plugins/gecko-mediaplayer-wmp.so
/usr/lib/firefox/plugins/gecko-mediaplayer.so
/usr/lib/firefox/plugins/nphelix.so
/usr/lib/firefox/plugins/nphelix.xpt
/usr/lib/firefox-3.6.3/.autoreg
/usr/lib/firefox-3.6.3/abrowser
/usr/lib/firefox-3.6.3/application.ini
/usr/lib/firefox-3.6.3/blocklist.xml
/usr/lib/firefox-3.6.3/browserconfig.properties
/usr/lib/firefox-3.6.3/chrome
/usr/lib/firefox-3.6.3/components
/usr/lib/firefox-3.6.3/defaults
/usr/lib/firefox-3.6.3/dictionaries
/usr/lib/firefox-3.6.3/distribution
/usr/lib/firefox-3.6.3/extensions
/usr/lib/firefox-3.6.3/ffox-beta-profile-migration-dialog
/usr/lib/firefox-3.6.3/firefox
/usr/lib/firefox-3.6.3/firefox-
/usr/lib/firefox-3.6.3/firefox-bin
/usr/lib/firefox-3.6.3/firefox-restart-required.update-notifier
/usr/lib/firefox-3.6.3/firefox.sh
/usr/lib/firefox-3.6.3/greprefs
/usr/lib/firefox-3.6.3/icons
/usr/lib/firefox-3.6.3/libfreebl3.chk
/usr/lib/firefox-3.6.3/libfreebl3.so
/usr/lib/firefox-3.6.3/libmozjs.so
/usr/lib/firefox-3.6.3/libnspr4.so
/usr/lib/firefox-3.6.3/libnss3.so
/usr/lib/firefox-3.6.3/libnssckbi.so
/usr/lib/firefox-3.6.3/libnssdbm3.chk
/usr/lib/firefox-3.6.3/libnssdbm3.so
/usr/lib/firefox-3.6.3/libnssutil3.so
/usr/lib/firefox-3.6.3/libplc4.so
/usr/lib/firefox-3.6.3/libplds4.so
/usr/lib/firefox-3.6.3/libsmime3.so
/usr/lib/firefox-3.6.3/libsoftokn3.chk
/usr/lib/firefox-3.6.3/libsoftokn3.so
/usr/lib/firefox-3.6.3/libsqlite3.so
/usr/lib/firefox-3.6.3/libssl3.so
/usr/lib/firefox-3.6.3/libxpcom.so
/usr/lib/firefox-3.6.3/libxul.so
/usr/lib/firefox-3.6.3/modules
/usr/lib/firefox-3.6.3/platform.ini
/usr/lib/firefox-3.6.3/plugins
/usr/lib/firefox-3.6.3/res
/usr/lib/firefox-3.6.3/run-mozilla.sh
/usr/lib/firefox-3.6.3/searchplugins
/usr/lib/firefox-3.6.3/chrome/browser-branding-en-US.jar
/usr/lib/firefox-3.6.3/chrome/browser-branding-en-US.manifest
/usr/lib/firefox-3.6.3/chrome/browser-branding.jar
/usr/lib/firefox-3.6.3/chrome/browser-branding.manifest
/usr/lib/firefox-3.6.3/chrome/browser.jar
/usr/lib/firefox-3.6.3/chrome/browser.manifest
/usr/lib/firefox-3.6.3/chrome/classic.jar
/usr/lib/firefox-3.6.3/chrome/classic.manifest
/usr/lib/firefox-3.6.3/chrome/comm.jar
/usr/lib/firefox-3.6.3/chrome/comm.manifest
/usr/lib/firefox-3.6.3/chrome/en-US.jar
/usr/lib/firefox-3.6.3/chrome/en-US.manifest
/usr/lib/firefox-3.6.3/chrome/icons
/usr/lib/firefox-3.6.3/chrome/pippki.jar
/usr/lib/firefox-3.6.3/chrome/pippki.manifest
/usr/lib/firefox-3.6.3/chrome/toolkit.jar
/usr/lib/firefox-3.6.3/chrome/toolkit.manifest
/usr/lib/firefox-3.6.3/chrome/icons/default
/usr/lib/firefox-3.6.3/chrome/icons/default/default16.png
/usr/lib/firefox-3.6.3/chrome/icons/default/default32.png
/usr/lib/firefox-3.6.3/chrome/icons/default/default48.png
/usr/lib/firefox-3.6.3/components/FeedConverter.js
/usr/lib/firefox-3.6.3/components/FeedProcessor.js
/usr/lib/firefox-3.6.3/components/FeedWriter.js
/usr/lib/firefox-3.6.3/components/GPSDGeolocationProvider.js
/usr/lib/firefox-3.6.3/components/NetworkGeolocationProvider.js
/usr/lib/firefox-3.6.3/components/WebContentConverter.js
/usr/lib/firefox-3.6.3/components/browser.xpt
/usr/lib/firefox-3.6.3/components/compreg.dat
/usr/lib/firefox-3.6.3/components/fuelApplication.js
/usr/lib/firefox-3.6.3/components/jsconsole-clhandler.js
/usr/lib/firefox-3.6.3/components/libbrowsercomps.so
/usr/lib/firefox-3.6.3/components/libbrowserdirprovider.so
/usr/lib/firefox-3.6.3/components/libdbusservice.so
/usr/lib/firefox-3.6.3/components/libimgicon.so
/usr/lib/firefox-3.6.3/components/libmozgnome.so
/usr/lib/firefox-3.6.3/components/libnkgnomevfs.so
/usr/lib/firefox-3.6.3/components/nsAddonRepository.js
/usr/lib/firefox-3.6.3/components/nsBadCertHandler.js
/usr/lib/firefox-3.6.3/components/nsBlocklistService.js
/usr/lib/firefox-3.6.3/components/nsBrowserContentHandler.js
/usr/lib/firefox-3.6.3/components/nsBrowserGlue.js
/usr/lib/firefox-3.6.3/components/nsContentDispatchChooser.js
/usr/lib/firefox-3.6.3/components/nsContentPrefService.js
/usr/lib/firefox-3.6.3/components/nsDefaultCLH.js
/usr/lib/firefox-3.6.3/components/nsDownloadManagerUI.js
/usr/lib/firefox-3.6.3/components/nsExtensionManager.js
/usr/lib/firefox-3.6.3/components/nsFilePicker.js
/usr/lib/firefox-3.6.3/components/nsFormAutoComplete.js
/usr/lib/firefox-3.6.3/components/nsHandlerService.js
/usr/lib/firefox-3.6.3/components/nsHelperAppDlg.js
/usr/lib/firefox-3.6.3/components/nsLivemarkService.js
/usr/lib/firefox-3.6.3/components/nsLoginInfo.js
/usr/lib/firefox-3.6.3/components/nsLoginManager.js
/usr/lib/firefox-3.6.3/components/nsLoginManagerPrompter.js
/usr/lib/firefox-3.6.3/components/nsMicrosummaryService.js
/usr/lib/firefox-3.6.3/components/nsPlacesAutoComplete.js
/usr/lib/firefox-3.6.3/components/nsPlacesDBFlush.js
/usr/lib/firefox-3.6.3/components/nsPlacesTransactionsService.js
/usr/lib/firefox-3.6.3/components/nsPrivateBrowsingService.js
/usr/lib/firefox-3.6.3/components/nsProxyAutoConfig.js
/usr/lib/firefox-3.6.3/components/nsSafebrowsingApplication.js
/usr/lib/firefox-3.6.3/components/nsSearchService.js
/usr/lib/firefox-3.6.3/components/nsSearchSuggestions.js
/usr/lib/firefox-3.6.3/components/nsSessionStartup.js
/usr/lib/firefox-3.6.3/components/nsSessionStore.js
/usr/lib/firefox-3.6.3/components/nsSetDefaultBrowser.js
/usr/lib/firefox-3.6.3/components/nsSidebar.js
/usr/lib/firefox-3.6.3/components/nsTaggingService.js
/usr/lib/firefox-3.6.3/components/nsTryToClose.js
/usr/lib/firefox-3.6.3/components/nsURLFormatter.js
/usr/lib/firefox-3.6.3/components/nsUpdateTimerManager.js
/usr/lib/firefox-3.6.3/components/nsUrlClassifierLib.js
/usr/lib/firefox-3.6.3/components/nsUrlClassifierListManager.js
/usr/lib/firefox-3.6.3/components/nsWebHandlerApp.js
/usr/lib/firefox-3.6.3/components/pluginGlue.js
/usr/lib/firefox-3.6.3/components/storage-Legacy.js
/usr/lib/firefox-3.6.3/components/storage-mozStorage.js
/usr/lib/firefox-3.6.3/components/txEXSLTRegExFunctions.js
/usr/lib/firefox-3.6.3/components/xpti.dat
/usr/lib/firefox-3.6.3/defaults/autoconfig
/usr/lib/firefox-3.6.3/defaults/pref
/usr/lib/firefox-3.6.3/defaults/profile
/usr/lib/firefox-3.6.3/defaults/syspref
/usr/lib/firefox-3.6.3/defaults/autoconfig/platform.js
/usr/lib/firefox-3.6.3/defaults/autoconfig/prefcalls.js
/usr/lib/firefox-3.6.3/defaults/pref/channel-prefs.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox-branding.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox-l10n.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox.js
/usr/lib/firefox-3.6.3/defaults/pref/kde.js
/usr/lib/firefox-3.6.3/defaults/pref/ubuntu-useragent.js
/usr/lib/firefox-3.6.3/distribution/distribution.ini
/usr/lib/firefox-3.6.3/distribution/searchplugins
/usr/lib/firefox-3.6.3/greprefs/all.js
/usr/lib/firefox-3.6.3/greprefs/security-prefs.js
/usr/lib/firefox-3.6.3/greprefs/xpinstall.js
/usr/lib/firefox-3.6.3/icons/document.png
/usr/lib/firefox-3.6.3/icons/mozicon128.png
/usr/lib/firefox-3.6.3/modules/CertUtils.jsm
/usr/lib/firefox-3.6.3/modules/DownloadLastDir.jsm
/usr/lib/firefox-3.6.3/modules/DownloadUtils.jsm
/usr/lib/firefox-3.6.3/modules/FileUtils.jsm
/usr/lib/firefox-3.6.3/modules/ISO8601DateUtils.jsm
/usr/lib/firefox-3.6.3/modules/LightweightThemeConsumer.jsm
/usr/lib/firefox-3.6.3/modules/LightweightThemeManager.jsm
/usr/lib/firefox-3.6.3/modules/Microformats.js
/usr/lib/firefox-3.6.3/modules/NetUtil.jsm
/usr/lib/firefox-3.6.3/modules/NetworkPrioritizer.jsm
/usr/lib/firefox-3.6.3/modules/PlacesDBUtils.jsm
/usr/lib/firefox-3.6.3/modules/PluralForm.jsm
/usr/lib/firefox-3.6.3/modules/SpatialNavigation.js
/usr/lib/firefox-3.6.3/modules/WindowDraggingUtils.jsm
/usr/lib/firefox-3.6.3/modules/XPCOMUtils.jsm
/usr/lib/firefox-3.6.3/modules/ctypes.jsm
/usr/lib/firefox-3.6.3/modules/debug.js
/usr/lib/firefox-3.6.3/modules/distribution.js
/usr/lib/firefox-3.6.3/modules/openLocationLastURL.jsm
/usr/lib/firefox-3.6.3/modules/utils.js
/usr/lib/firefox-3.6.3/res/EditorOverride.css
/usr/lib/firefox-3.6.3/res/arrow.gif
/usr/lib/firefox-3.6.3/res/arrowd.gif
/usr/lib/firefox-3.6.3/res/broken-image.png
/usr/lib/firefox-3.6.3/res/charsetData.properties
/usr/lib/firefox-3.6.3/res/charsetalias.properties
/usr/lib/firefox-3.6.3/res/contenteditable.css
/usr/lib/firefox-3.6.3/res/designmode.css
/usr/lib/firefox-3.6.3/res/dtd
/usr/lib/firefox-3.6.3/res/entityTables
/usr/lib/firefox-3.6.3/res/fonts
/usr/lib/firefox-3.6.3/res/forms.css
/usr/lib/firefox-3.6.3/res/grabber.gif
/usr/lib/firefox-3.6.3/res/hiddenWindow.html
/usr/lib/firefox-3.6.3/res/html
/usr/lib/firefox-3.6.3/res/html.css
/usr/lib/firefox-3.6.3/res/langGroups.properties
/usr/lib/firefox-3.6.3/res/language.properties
/usr/lib/firefox-3.6.3/res/loading-image.png
/usr/lib/firefox-3.6.3/res/mathml.css
/usr/lib/firefox-3.6.3/res/quirk.css
/usr/lib/firefox-3.6.3/res/svg.css
/usr/lib/firefox-3.6.3/res/table-add-column-after-active.gif
/usr/lib/firefox-3.6.3/res/table-add-column-after-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-column-after.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before-active.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after-active.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before-active.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before.gif
/usr/lib/firefox-3.6.3/res/table-remove-column-active.gif
/usr/lib/firefox-3.6.3/res/table-remove-column-hover.gif
/usr/lib/firefox-3.6.3/res/table-remove-column.gif
/usr/lib/firefox-3.6.3/res/table-remove-row-active.gif
/usr/lib/firefox-3.6.3/res/table-remove-row-hover.gif
/usr/lib/firefox-3.6.3/res/table-remove-row.gif
/usr/lib/firefox-3.6.3/res/ua.css
/usr/lib/firefox-3.6.3/res/unixcharset.properties
/usr/lib/firefox-3.6.3/res/viewsource.css
/usr/lib/firefox-3.6.3/res/dtd/mathml.dtd
/usr/lib/firefox-3.6.3/res/dtd/xhtml11.dtd
/usr/lib/firefox-3.6.3/res/entityTables/html40Latin1.properties
/usr/lib/firefox-3.6.3/res/entityTables/html40Special.properties
/usr/lib/firefox-3.6.3/res/entityTables/html40Symbols.properties
/usr/lib/firefox-3.6.3/res/entityTables/htmlEntityVersions.properties
/usr/lib/firefox-3.6.3/res/entityTables/mathml20.properties
/usr/lib/firefox-3.6.3/res/entityTables/transliterate.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfont.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontSTIXNonUnicode.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontSTIXSize1.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontStandardSymbolsL.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontUnicode.properties
/usr/lib/firefox-3.6.3/res/html/folder.png
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-addons/searchplugins
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/icon.png
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/preview.png
/usr/lib/firefox-addons/searchplugins/common
/usr/lib/firefox-addons/searchplugins/en-US
/usr/lib/firefox-addons/searchplugins/en-US/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/en-US/answers.xml
/usr/lib/firefox-addons/searchplugins/en-US/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/en-US/eBay.xml
/usr/lib/firefox-addons/searchplugins/en-US/google.xml
/usr/lib/firefox-addons/searchplugins/en-US/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/en-US/yahoo.xml
/usr/lib/mozilla-firefox/plugins
/usr/lib/mozilla-firefox/plugins/gxineplugin.so
/usr/share/firefox
/usr/share/app-install/desktop/firefox-greasemonkey.desktop
/usr/share/app-install/desktop/firefox-launchpad-plugin.desktop
/usr/share/app-install/desktop/firefox-ubuntu-it-menu.desktop
/usr/share/app-install/desktop/firefox-webdeveloper.desktop
/usr/share/app-install/desktop/firefox.desktop
/usr/share/app-install/icons/firefox-greasemonkey.xpm
/usr/share/app-install/icons/firefox-installer.png
/usr/share/app-install/icons/firefox-launchpad-plugin.xpm
/usr/share/app-install/icons/firefox-themes-ubuntu.xpm
/usr/share/app-install/icons/firefox-ubuntu-it-menu.png
/usr/share/app-install/icons/firefox-webdeveloper.xpm
/usr/share/applications/firefox.desktop
/usr/share/apport/package-hooks/firefox.py
/usr/share/bug/firefox
/usr/share/bug/firefox/presubj
/usr/share/doc/firefox
/usr/share/doc/firefox-branding
/usr/share/doc/firefox-gnome-support
/usr/share/doc/firefox/MPL.gz
/usr/share/doc/firefox/README.Debian
/usr/share/doc/firefox/changelog.Debian.gz
/usr/share/doc/firefox/copyright
/usr/share/doc/firefox/firefox.cfg
/usr/share/doc/firefox-branding/changelog.Debian.gz
/usr/share/doc/firefox-branding/copyright
/usr/share/doc/firefox-gnome-support/changelog.Debian.gz
/usr/share/doc/firefox-gnome-support/copyright
/usr/share/firefox/defaults
/usr/share/firefox/defaults/pref
/usr/share/firefox/defaults/pref/apturl.js
/usr/share/menu/firefox
/usr/share/pixmaps/firefox.png
/usr/share/xfce4/helpers/firefox.desktop
/var/lib/dpkg/info/firefox-branding.list
/var/lib/dpkg/info/firefox-branding.md5sums
/var/lib/dpkg/info/firefox-gnome-support.list
/var/lib/dpkg/info/firefox-gnome-support.md5sums
/var/lib/dpkg/info/firefox-gnome-support.postinst
/var/lib/dpkg/info/firefox-gnome-support.prerm
/var/lib/dpkg/info/firefox.conffiles
/var/lib/dpkg/info/firefox.list
/var/lib/dpkg/info/firefox.md5sums
/var/lib/dpkg/info/firefox.postinst
/var/lib/dpkg/info/firefox.postrm
/var/lib/dpkg/info/firefox.preinst
/var/lib/dpkg/info/firefox.prerm
justin@justin-desktop:~$ 


---

### Post by lovinglinux on 2010-06-02
There is nothing in your output that I can identify as a possible culprit.

Try to use FLASH-AID again (make sure you get the latest version) and then post the output of:

```
locate libflashplayer.so
```

---

### Post by gandaran on 2010-06-02
> justin@justin-desktop:~$ locate libflashplayer.so
/home/justin/libflashplayer.so
/home/justin/Desktop/libflashplayer.so
justin@justin-desktop:~$
you don't have any flash installed! are you sure you installed it?
what you have is the plugin (libflashplayer.so) in your desktop and home folder.

---

### Post by lovinglinux on 2010-06-02
> **gandaran said:**
> you don't have any flash installed! are you sure you installed it?
what you have is the plugin (libflashplayer.so) in your desktop and home folder.

Yes. Is not installed. That's why I want to see the output of locate libflashplayer.so after using FLASH-AID.

---

### Post by agentchange on 2010-06-02
I was going to ask about those missing .so files compared to other installations, but I think I have figured out the problem, perhaps.  I installed using flash-aid (it is no longer residing in the search firefox add-ons, fyi) and here is my ouput again.

> justin@justin-desktop:/opt$ locate libflashplayer.so
/home/justin/libflashplayer.so
/home/justin/Desktop/libflashplayer.so
justin@justin-desktop:/opt$ 
 

However, I had been reading this other [thread]("http://ubuntuforums.org/showthread.php?t=715604") which showed me how to get flash going in konqueror for mythbrowser, but it did not get hulu to work for me like it did for them, though the youtube worked.  What I know from that installation is that there should be an .so file in /opt/flash/ because I put it there, but it is not showing up in locate.  Lastly, the only reason I can think of why that would happen is because brilliant genius me decided to get creative (something about gaming? something I read about) and made /home/ a separate partition! which probably explains a lot more.

So many of the installs wind up where they are supposed to on the root partition, but for some reason locate is not seeing that file (that command is not capable of crossing the partition barrier and others are?)  Is that why none of these flash installations are crossing that barrier, but then Synaptic should accomplish that because it has installed so much other stuff there.  Actually, /usr/bin/ is only 200 MB which seems kind of low.  Not sure how much I have installed yet but kate is there which I remember.  I downloaded lots of multimedia apps which are obviously somewhere else.  OK, can you make some sense of this?  How do I make this work?  Is it fixable?

---

### Post by lovinglinux on 2010-06-02
> **agentchange said:**
> I installed using flash-aid (it is no longer residing in the search firefox add-ons, fyi) and here is my ouput again.

I guess because I just received an e-mail saying it has been approved by Mozilla, so I guess the site cache didn't update the status of the extension yet. Nevertheless, you can get it from my site.

> **agentchange said:**
> However, I had been reading this other [thread]("http://ubuntuforums.org/showthread.php?t=715604") which showed me how to get flash going in konqueror for mythbrowser, but it did not get hulu to work for me like it did for them, though the youtube worked.  What I know from that installation is that there should be an .so file in /opt/flash/ because I put it there, but it is not showing up in locate.  Lastly, the only reason I can think of why that would happen is because brilliant genius me decided to get creative (something about gaming? something I read about) and made /home/ a separate partition! which probably explains a lot more.

So many of the installs wind up where they are supposed to on the root partition, but for some reason locate is not seeing that file (that command is not capable of crossing the partition barrier and others are?)  Is that why none of these flash installations are crossing that barrier, but then Synaptic should accomplish that because it has installed so much other stuff there.  Actually, /usr/bin/ is only 200 MB which seems kind of low.  Not sure how much I have installed yet but kate is there which I remember.  I downloaded lots of multimedia apps which are obviously somewhere else.  OK, can you make some sense of this?  How do I make this work?  Is it fixable?

Is hard to tell since I don't know what you have already done to your system. Having a separate home is not an obstacle. I have separate home and multiple partitions to store data that is linked to home, but not physically stored there. Everything works fine. Nevertheless, I don't understand why you have /opt/flash. Have you diverted the plugin installation folder to that location? That could be the issue.

What else Firefox related do you have in /opt?

---

### Post by agentchange on 2010-06-02
Only home is separate.  I put that in /opt/flash/ because thats what this guy did to make it work in konqueror.  Looking back, he looks pretty young.  No. I just cut and pasted it there.  Have not done anything else out of the ordinary and that was practically the last thing I did.  Don't even know how to divert the plugin folder.

---

### Post by lovinglinux on 2010-06-02
> **agentchange said:**
> Only home is separate.  I put that in /opt/flash/ because thats what this guy did to make it work in konqueror.  Looking back, he looks pretty young.  No. I just cut and pasted it there.  Have not done anything else out of the ordinary and that was practically the last thing I did.  Don't even know how to divert the plugin folder.

That's good.

Paste the output of

```
ls /usr/lib/mozilla/plugins/
```

---

### Post by agentchange on 2010-06-02
flashplugin-alternative.so  gecko-mediaplayer.so      nphelix.so
gecko-mediaplayer-dvx.so    gecko-mediaplayer-wmp.so  nphelix.xpt
gecko-mediaplayer-qt.so     gxineplugin.so
gecko-mediaplayer-rm.so     libjavaplugin.so

---

### Post by lovinglinux on 2010-06-02
Now the output of these:

```
file /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

```
file /etc/alternatives/mozilla-flashplugin
```

```
ls /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
```

---

### Post by agentchange on 2010-06-02
justin@justin-desktop:~$ sudo file /usr/lib/mozilla/plugins/flashplugin-alternative.so

/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'

justin@justin-desktop:~$ sudo file /etc/alternatives/mozilla-flashplugin

/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'

justin@justin-desktop:~$ sudo ls /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

ls: cannot access /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: No such file or directory

justin@justin-desktop:~$

---

### Post by lovinglinux on 2010-06-02
Close Firefox and run these:

```
sudo apt-get purge swfdec-mozilla
```

```
sudo apt-get purge mozilla-plugin-gnash
```

```
sudo apt-get purge adobe-flashplugin
```

```
sudo apt-get purge flashplugin-nonfree
```

```
sudo apt-get purge flashplugin-installer
```

```
sudo apt-get purge nspluginwrapper
```

```
sudo apt-get install flashplugin-nonfree
```

Now open Firefox, type **about[noparse]:[/noparse]config**, type **plugin.expose_full_path** in the filter field, then double-click the **plugin.expose_full_path** in the resulting list until it shows true in the value column.

Then type **about[noparse]:[/noparse]plugins** in the address bar, locate Shockwave Flash and copy/paste the lines that specify the File and Version.

---

### Post by agentchange on 2010-06-02
That does not exist on this page.  I checked Synaptic, and I have pyvnc2swf and swfmill.

---

### Post by agentchange on 2010-06-02
and libimage-size-perl, if you count the lib files, all installed, but no Shockwave.  I think mythbuntu is supposed to be a really slimmed down package.  Do you think they left that out?

---

### Post by lovinglinux on 2010-06-02
What is the output of these now:

```
file /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

```
file /etc/alternatives/mozilla-flashplugin
```

```
ls /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
```

---

### Post by lovinglinux on 2010-06-02
> **agentchange said:**
> and libimage-size-perl, if you count the lib files, all installed, but no Shockwave.  I think mythbuntu is supposed to be a really slimmed down package.  Do you think they left that out?

I don't know. I never used Mythbuntu, but there is an issue with the symlinks to the flash plugin.

what is the output of:

```
uname -a
```

---

### Post by agentchange on 2010-06-02
> justin@justin-desktop:~$ sudo file /usr/lib/mozilla/plugins/flashplugin-alternative.so
[sudo] password for justin: 
/usr/lib/mozilla/plugins/flashplugin-alternative.so: Symbolic link to `/etc/alternatives/mozilla-flashplugin'

justin@justin-desktop:~$ sudo file /etc/alternatives/mozilla-flashplugin
/etc/alternatives/mozilla-flashplugin: Symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'

justin@justin-desktop:~$ sudo ls /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
ls: Cannot access /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: No such file or directory


> justin@justin-desktop:~$ uname -a
linux justin-desktop 2.6.32-22-generic #33-ubuntu smp wed apr 28 13:27:30 utc 2010 i686 gnu/linux
justin@justin-desktop:~$ 
1

---

### Post by lovinglinux on 2010-06-02
Ignore the error **ls: Cannot access /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: No such file or directory **. For some reason I was fixated with 64bit, which uses that file. I guess my brain is freezing with too many flash threads. Sorry.

Anyway, this is what is going on. Flash seems to be installed properly at /usr/lib/flashplugin-installer/libflashplayer.so and the necessary synlinks to /usr/lib/mozilla/plugins are in place. So the problem is that the browser is not recognizing it.

Close Firefox, then open ~/.mozilla/firefox and locate your default profile folder, then open it and rename the file pluginreg.dat to something like pluginreg.dat.old. Start Firefox and check if it can recognize the plugin. Also check if other plugins are displayed.

---

### Post by agentchange on 2010-06-02
So this npwrapper.libflashplayer.so file came up missing again and I keep running across a bunch of people claiming to be able to run shockwave on linux, but for some reason, it doesn't seem so easy.  Why?  Adobe just has to make money on some things.  What's the difference between Shockwave and Flash and is it even a concern to me?  I'm just trying to get flash to work.

---

### Post by lovinglinux on 2010-06-02
> **agentchange said:**
> So this npwrapper.libflashplayer.so file came up missing again...

Don' worry, that was my mistake. Your system shouldn't have npwrapper.libflashplayer.so. That is a file that exists only in 64bit machines running the 32bit version of flash.

> **agentchange said:**
> ...and I keep running across a bunch of people claiming to be able to run shockwave on linux, but for some reason, it doesn't seem so easy.  Why?  Adobe just has to make money on some things.

It shouldn't be that complicated. I'm trying to figure out why this is happening. Are you using Firefox or something like Swiftfox?

> **agentchange said:**
> What's the difference between Shockwave and Flash and is it even a concern to me? 

Same thing. No difference.


Please I forgot to ask you for the output of:

```
file /usr/lib/firefox-addons/plugins/libflashplayer.so
```

---

### Post by agentchange on 2010-06-02
Alright, thank you for the help.  I missed it the first time around but the .so file was missing from that location.  Duh.  Now it works.  So why doesn't the install package put it there like it's suppose to, using any one of the installers I have used?  Is there a registry type of file that records where this/these files are and if there are too many in different places from different installations, it borks or something?

---

### Post by lovinglinux on 2010-06-02
> **agentchange said:**
> Alright, thank you for the help.  I missed it the first time around but the .so file was missing from that location.  Duh.  Now it works.  So why doesn't the install package put it there like it's suppose to, using any one of the installers I have used?  Is there a registry type of file that records where this/these files are and if there are too many in different places from different installations, it borks or something?

I did several tests on both 64bit and 32bit machines and that file is not necessary and doesn't exists on a default Ubuntu Lucid Lynx machine. Nevertheless, I haven't tested Mythbuntu yet. I'm going to add it to my tool just as a precaution. I was already adding it when installing the 64bit beta anyway.

---

