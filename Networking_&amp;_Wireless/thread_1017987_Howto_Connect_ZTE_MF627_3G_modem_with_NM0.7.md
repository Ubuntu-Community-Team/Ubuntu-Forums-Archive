---
title: "Howto: Connect ZTE MF627 3G modem with NM0.7"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by jfernyhough on 2008-12-21
I recently bought a 3G mobile broadband modem and then realised I'd bought the wrong model - instead of getting a Huawei E160 or E169 that reportedly work OOTB with Intrepid I got a ZTE MF627 for which no information exists. On the plus side, it has a built-in MicroSD reader...

--EDIT

This should all now be taken care of by udev-extras. The modem will initially be detected as the ZeroCD device; after ejecting it from the desktop (or the Places sidebar in Nautilus) it will be re-detected as a modem.

$ sudo aptitude install udev-extras

---

I initially raised a bug [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310025") but in the meantime have got it working. So here is a how-to.

**1) Download and install usb_modeswitch**
Go [here]("http://www.draisberghof.de/usb_modeswitch/#download") and download the deb file. A direct link to version 0.9.5 is [here]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.5_i386.deb"). Then install it.

This provides a way of switching the USB modem from its initial useless mode to its correct, functional modes. It will need configuring to apply to the modem.

**2) Edit /etc/usb_modeswitch.conf to apply to the MF628+**

Either comment the first modem configuration out, then find and uncomment the section for the MF628+, or (more easily) replace the content of the file with:

```
########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
#
# Contributor: Joakim Wennergren
#
# Also applies to MF627 (Tested 3 UK) JF

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
```Save it.

**3) Create a udev rule to automatically run usb_modeswitch when the modem is plugged in**

Create a new file called 999-zte-rules:
gksudo gedit /etc/udev/rules.d/999-zte.rules

Its content should be as follows:
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/usr/sbin/usb_modeswitch"
```This will trigger usb_modeswitch every time you plug in the modem. Which is useful if you want it to work automatically.

**4) Add device information to HAL so network-manager recognises the device as a modem**

Finally, in order for Network Manager to recognise the modem information has to be added to HAL.

Create a new file:
gksudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi

Its content should be as follows:
```
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
      <!-- ZTE MF627 HSDPA USB dongle -->
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
            <append key="info.capabilities" type="strlist">modem</append>
          </match>
        </match>
      </match>
  </device>
</deviceinfo>
```Save it.

**5) Plug in the modem**
Make sure the SIM card is in the modem (and if you're using 3 UK make sure you're in a 3G area. otherwise it won't work) and plug it into your PC.

After several seconds the LED should light red as it powers up, then switch to blue when it finds a network. You can check it's working by checking dmesg: you should see entries for GSM modem, USB drive and CD drive. Once modeswitch has been triggered and the modem reboots you will be presented with the ZeroCD device (e.g. containing the 3connect software), a USB MicroSD card reader, and if everything has gone correctly, Network Manager will detect a new mobile broadband modem.

Feel free to ignore the ZeroCD device and unmount it from the desktop.

If everything has gone well dmesg should read something like:
```
[52022.169361] usb 5-1: new high speed USB device using ehci_hcd and address 31
[52022.169362] usb 5-1: configuration #1 chosen from 1 choice
[52022.172724] usb-storage: device ignored
[52079.232398] usb 5-1: USB disconnect, address 31
[52189.029694] usb 5-1: new high speed USB device using ehci_hcd and address 32
[52189.177064] usb 5-1: configuration #1 chosen from 1 choice
[52189.192061] usb-storage: device ignored
[52194.546308] usb 5-1: USB disconnect, address 32
[52200.032140] usb 5-1: new high speed USB device using ehci_hcd and address 33
[52200.183440] usb 5-1: configuration #1 chosen from 1 choice
[52200.184979] option 5-1:1.0: GSM modem (1-port) converter detected
[52200.185184] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[52200.185453] option 5-1:1.1: GSM modem (1-port) converter detected
[52200.185592] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[52200.200858] scsi28 : SCSI emulation for USB Mass Storage devices
[52200.204904] usb-storage: device found at 33
[52200.204909] usb-storage: waiting for device to settle before scanning
[52200.205113] option 5-1:1.3: GSM modem (1-port) converter detected
[52200.205304] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[52205.205580] usb-storage: device scan complete
[52205.207696] scsi 28:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[52205.210603] scsi 28:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[52205.226669] sd 28:0:0:0: [sdb] Attached SCSI removable disk
[52205.228914] sd 28:0:0:0: Attached scsi generic sg2 type 0
[52205.345654] sr1: scsi-1 drive
[52205.345837] sr 28:0:0:1: Attached scsi CD-ROM sr1
[52205.346023] sr 28:0:0:1: Attached scsi generic sg3 type 5
[52218.692468] ISO 9660 Extensions: Microsoft Joliet Level 1
[52218.699732] ISOFS: changing to secondary root
```

(I initially tried to post this in Tips and Tricks but it hasn't appeared yet. I'm posting it here so I at least have it as a record somewhere.)

---

### Post by spegru on 2009-01-07
Hi this looks useful.

Does this work with both Intrepid and Hardy and/or with network manager and the vodafone betavine application?

---

### Post by jfernyhough on 2009-01-07
I've tested this with both Intrepid and Jaunty - the same steps work on both. I've no idea whether this will work with Hardy - does Hardy have Network Manager 0.7?

No idea about the "betavine" program either - I just set up the system so the modem would be recognised natively.

---

### Post by liamgh on 2009-04-27
Had a go at automating the steps above, details in this blog post: [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way).

---

### Post by Fazl on 2009-05-03
Liam, i tried your method but the file didn't work. Its ok though. I followed jfernyhough's method step by step and FINALLY got my problem resolved! Wow, four days of messing with this thing and finally, I got it working. Thanks jfernyhough!

---

### Post by liamgh on 2009-05-03
Hi Fazl, what happened when you tried the file? Did it install ok?

---

### Post by pedroquaresma on 2009-07-07
Hi

I've tried to apply the same procedure to a ZON Connection (Portugal), under Debian.

It's the same device MF627... but I need a PIN code. Is that important (it should be :)?

I've installed the zte-mf627-switch_0.1_all.deb and usb-modeswitch_1.0.2-1_i386.deb, without problems.

The procedure seems to work, the MF627 device change from 

Bus 005 Device 008: ID 19d2:2000 ONDA Communication S.p.A.

to

Bus 005 Device 009: ID 19d2:0031 ONDA Communication S.p.A.

but the modem does not seems to became active (the light it is still red.

[ 4660.434370] usb 5-3: new high speed USB device using ehci_hcd and address 8
[ 4660.589484] usb 5-3: configuration #1 chosen from 1 choice
[ 4660.591419] usb-storage: device ignored
[ 4660.591419] usb 5-3: New USB device found, idVendor=19d2, idProduct=2000
[ 4660.591419] usb 5-3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[ 4660.591419] usb 5-3: Product: ZTE CDMA Technologies MSM
[ 4660.591419] usb 5-3: Manufacturer: ZTE,Incorporated
[ 4660.591419] usb 5-3: SerialNumber: 1234567890ABCDEF
[ 4666.493794] usb 5-3: USB disconnect, address 8
[ 4672.828876] usb 5-3: new high speed USB device using ehci_hcd and address 9
[ 4672.975249] usb 5-3: configuration #1 chosen from 1 choice
[ 4672.979994] scsi8 : SCSI emulation for USB Mass Storage devices
[ 4672.984988] usb-storage: device found at 9
[ 4672.984988] usb-storage: waiting for device to settle before scanning
[ 4672.979994] usb 5-3: New USB device found, idVendor=19d2, idProduct=0031
[ 4672.979994] usb 5-3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[ 4672.979994] usb 5-3: Product: ZTE CDMA Technologies MSM
[ 4672.979994] usb 5-3: Manufacturer: ZTE,Incorporated
[ 4678.207652] usb-storage: device scan complete
[ 4678.210651] scsi 8:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[ 4678.255654] sd 8:0:0:0: [sdb] Attached SCSI removable disk

do you have any ideia what to change? How and where the PIN code came to action?

Any help will be deeply appreciated.

Thank you (Obrigado)

---

### Post by Hairy_Palms on 2009-07-18
just got this modem the other day, turns out my ZTE has actual linux software on the mass storage part!, its written in qt3 so it looks kindof ugly but at least the vendor is actually providing linux software, i cant attach it here as its 8MB in size, it depends on libqt3-mt and wvdial 
i sent an email to three asking if there was a download location for the software but didnt get a response and it isnt available at 

[http://www.three.com.au/cs/ContentServer?c=Page&pagename=Three%2FPage%2FBusinessVideoCallingTemplate&cid=1215747787891](http://www.three.com.au/cs/ContentServer?c=Page&pagename=Three%2FPage%2FBusinessVideoCallingTemplate&cid=1215747787891)

ive put it on rapidshare so anyone with this modem can benefit from it [http://rapidshare.com/files/257164233/3ukpclin.gz.html](http://rapidshare.com/files/257164233/3ukpclin.gz.html)

---

### Post by jfernyhough on 2009-07-18
Does that thing actually work? I tried it initially and it wouldn't even load... though having said that, I'm also trying it on x86_64 not i386 which could likely be an issue.

---

### Post by Hairy_Palms on 2009-07-28
the software is i386 only as far as i know but it works fine here

---

### Post by Shmee on 2009-09-19
Hairy_Palms,
is there any chance of you making that file available again?

---

### Post by Jimmy9pints on 2009-10-05
> ive put it on rapidshare so anyone with this modem can benefit from it [http://rapidshare.com/files/257164233/3ukpclin.gz.html](http://rapidshare.com/files/257164233/3ukpclin.gz.html)

Could anyone re-up this?

Thanks

---

### Post by Peter Kropotkin on 2010-01-19
**[FONT=Arial][SIZE=3]Instalação da Zon Net Mobile em Ubuntu[/SIZE][/FONT]**
 
[FONT=Arial][SIZE=3]Depois de algumas batalhas inglórias. Depois de ler aproximadamente uma 50 páginas. Depois de…[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Parece que cheguei a um procedimento para instalação desta coisa.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Note-se que as condições em que testei esta instalação são as seguintes:[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=3]Ubuntu Desktop 9.10 32-bit (em inglês)[/SIZE][/FONT]
[FONT=Arial][SIZE=3]ZON Net Mobile Zero (modem ZTE MF627)[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=3]Bem, aqui vão os passos todos de instalação e configuração:[/SIZE][/FONT]
 
> **[FONT=Arial][SIZE=3]1 - Instalar "usb-modeswitch". Este componente vai possibilitar comutar o modo inicial do ZON Mobile (simples pen) para o modo desejado (modem)[/SIZE][/FONT]**[FONT=Arial][SIZE=3]
[/SIZE][/FONT]```
sudo apt-get install usb-modeswitch
```> **[FONT=Arial][SIZE=3]2 - Editar "/etc/usb_modeswitch.conf" usando o Gedit[/SIZE][/FONT]**```
gksudo gedit /etc/usb_modeswitch.conf
```[INDENT][FONT=Arial][SIZE=3]No final do ficheiro (se bem que pode ser em qualquer ponto do ficheiro) acrescentar o seguinte conteúdo[/SIZE][/FONT]
[/INDENT]```
# ZTE MF627
#
# Contributor: Joakim Wennergren
 
DefaultVendor= 0x19d2
DefaultProduct= 0x2000
 
TargetVendor= 0x19d2
TargetProduct= 0x0031
 
MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
 
```> **[FONT=Arial][SIZE=3]3 - Criar uma "udev rule" (usando o Gedit ) para que seja executado o "usb_modeswitch" quando o modem é ligado. Desta forma automatiza-se a comutação do modo "pen" para o modo "modem"[/SIZE][/FONT]**```
gksudo gedit /etc/udev/rules.d/999-zte.rules
```[INDENT][FONT=Arial][SIZE=3]O Gedit abre um novo ficheiro vazio. Acrescente o seguinte conteúdo[/SIZE][/FONT]
[/INDENT]```
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/usr/sbin/usb_modeswitch"
```> **[FONT=Arial][SIZE=3]4 - Acrescentar uma "device information" ao "HAL" (usando o Gedit) para que o "network-manager" reconheça o "modem"[/SIZE][/FONT]**
 ```
gksudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi
```[INDENT][FONT=Arial][SIZE=3]O Gedit abre um novo ficheiro vazio. Acrescente o seguinte conteúdo[/SIZE][/FONT]
[/INDENT]```
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- ZTE MF627 HSDPA USB dongle -->
<match key="@info.parent:usb.vendor_id" int="0x19d2">
<match key="@info.parent:usb.product_id" int="0x0031">
<match key="@info.parent:usb.interface.number" int="3">
<append key="modem.command_sets" type="strlist">GSM-07.07</append>
<append key="modem.command_sets" type="strlist">GSM-07.05</append>
<append key="info.capabilities" type="strlist">modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>
```> **[FONT=Arial][SIZE=3]5 - Ligar o “modem” (depois de reiniciar o computador[/SIZE][/FONT]**[INDENT][FONT=Arial][SIZE=3]Reinicie o computador[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Ligue o "modem". Após algum tempo o LED acende-se com cor vermelha, depois apaga e volta a acender o LED ainda com cor vermelha. (Ao contrário do que é indicado em muitas páginas sobre este assunto, o LED não fica azul nesta fase porque o PIN ainda não foi enviado para o "modem")[/SIZE][/FONT]
[/INDENT]> **[FONT=Arial][SIZE=3]6 - Criar a ligação de rede[/SIZE][/FONT]**[INDENT][FONT=Arial][SIZE=3]Abra o menu "System -> Preferences -> Network Connections"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Abra o "tab" "Mobile Broadband"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique no botão "Add"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]A janela mostra (se tudo correu bem até aqui) uma "Combo Box" indicando "ZTE Incorporated ZTE CDMA Technologies MSM"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique no botão "Forward"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Escolha o país (Portugal)[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique no botão "Forward"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Na janela apresentada seleccione "I can't find my provider and I wish to enter it manualy"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Na caixa de texto "Provider:" escreva "ZON" (em boa verdade acho que pode escrever o que entender)[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique no botão "Forward"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Na caixa "Select plan APN" escreva "internet.zon.pt"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique no botão "Forward"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique no botão "Apply"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]De volta ao "tab" "Mobile Broadband" deverá ver uma entrada "ZON Connection 1" (ou coisa parecida)[/SIZE][/FONT]
[/INDENT]> **[FONT=Arial][SIZE=3]7 - Configurar a ligação de rede[/SIZE][/FONT]**[INDENT][FONT=Arial][SIZE=3]Ainda no "tab" "Mobile Broadband" seleccione a entrada "ZON Connection 1" e clique o botão "Edit"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]No "tab" "Mobile Broadband" preencha apenas a caixa "PIN" com o PIN que é indicado no cartão da ZON Mobile[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Seleccione agora o "tab" "PPP Settings"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique o botão "Configure Methods..."[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Na nova janela marcar apenas "CHAP" (é provável que tenha que desmarcar todas as outras opções)[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique o botão "OK"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Seleccione agora o "tab" "IPv4 Settings"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Na "Combo Box" "Method" seleccione "Automatic PPP addresses only"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Na caixa "DNS servers" escreva "212.18.160.133, 212.18.160.134"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique no botão "Apply"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Feche todas as janelas[/SIZE][/FONT]
[/INDENT]> **[FONT=Arial][SIZE=3]8 - E[/SIZE][/FONT]****[FONT=Arial][SIZE=3]stabelecer ligação[/SIZE][/FONT]**[INDENT][FONT=Arial][SIZE=3]Estabelecer a ligação é um procedimento idêntico ao de ligar a uma rede "wireless"[/SIZE][/FONT]
[/INDENT][INDENT][FONT=Arial][SIZE=3]Clique no icon de rede (no conjunto de icons à direita da barra superior) e escolha "ZON Connection 1"[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=3]
[/SIZE][/FONT]> [FONT=Arial][SIZE=3]Créditos e referências:[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=3]Joakim Wennergren[/SIZE][/FONT]
[FONT=Arial][SIZE=3]gnrtuga[/SIZE][/FONT]
[[FONT=Arial][SIZE=3]http://ubuntuforums.org/showthread.php?t=1017630[/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1017630")
[[FONT=Arial][SIZE=3]http://ubuntuforums.org/showthread.php?t=1209582[/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1209582")
[/INDENT][FONT=Arial][SIZE=3]Peter Kropotkin[/SIZE][/FONT]

---

