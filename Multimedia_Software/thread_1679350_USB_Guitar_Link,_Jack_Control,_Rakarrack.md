---
title: "USB Guitar Link, Jack Control, Rakarrack"
date: 2011-01-31
forum: Multimedia Software
---

### Post by tman69 on 2011-01-31
In the interest of full disclosure I am basically a *Linux Noob*

I am running Ubuntu 10.10 (2.6.35-24-generic). The goal is to use my USB Guitar Link adapter through Jack Control then through Rakarrack. The problem is I cannot get Jack Control configured correctly to send the USB input to Rakarrack. I have searched and searched to try and find a solution and attempted to follow any ideas that had been offered to others but still no luck. Here is the output of the lsusb command:


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I currently have Jack Control interface set to default.

Thanks
Tim

---

### Post by cchhrriiss121212 on 2011-02-01
Could you show what aplay -l gives you from a terminal?

---

### Post by tman69 on 2011-02-01
I am at work currently but I will as soon as I get home this afternoon. Should this be done with the USB Guitar Link connected and Jack Control running?

---

### Post by cchhrriiss121212 on 2011-02-01
Just plug the device in, it is not jack related. Also post arecord -l just to be sure.

---

### Post by tman69 on 2011-02-01
Here are the results for aplay:


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Here is arecord:

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by cchhrriiss121212 on 2011-02-01
OK, that shows that your USB device is recognised and named hw:1, try selecting it instead of "default" under the interface setting in jack control setup window.

---

### Post by tman69 on 2011-02-01
Okay, tried that and still Rakarrack not getting the guitar input.

Trying to paste screenshots but having issues.

---

### Post by cchhrriiss121212 on 2011-02-02
Try opening alsamixer from a terminal window then check the volume levels, then open jack, press start and tell me what connections you see in the connection window.

---

### Post by tman69 on 2011-02-02
Okay here is aslamixer:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: SigmaTel STAC9205                              F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: 0.00]                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                          &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;    Mic In    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;   Digital     &#9474;
&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;                       &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                       &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9474;
&#9474;     100    100<>100 100<>100 100<>100                                        &#9474;
&#9474;  < Master >Headphon Speaker    PCM    Mic Jack  S/PDIF  S/PDIF D S/PDIF P    &#9474;

---

### Post by tman69 on 2011-02-02
After starting Jack I see the following readable connections:

Under Audio - capture_1 and capture_2 both with a mic icon next to them

Under Midi - nothing

Under ALSA - 0:Midi Through port-0

---

### Post by cchhrriiss121212 on 2011-02-02
When running alsamixer, press f6 to select the USB device, then use arrow keys to change the volume level. If that makes no difference, post what you see in the jack message window.

---

### Post by tman69 on 2011-02-02
Okay, the USB was set to 80 so I changed it to 100. Here is a copy/paste of the Jack messages.

Jack: fPollTable i = 1 fd = 7
Jack: JackSocketServerChannel::ClientCreate socket
Jack: JackSocketServerChannel::BuildPoolTable size = 3
Jack: fSocketTable i = 1 fd = 7
Jack: fSocketTable i = 2 fd = 10
Jack: fPollTable i = 1 fd = 7
Jack: fPollTable i = 2 fd = 10
Jack: Poll client error err = Success
Jack: JackSocketServerChannel::ClientKill ref = -1
Jack: Client was not opened : probably correspond to server_check
Jack: JackClientSocket::Close
Jack: JackSocketServerChannel::ClientCreate socket
Jack: JackSocketServerChannel::BuildPoolTable size = 3
Jack: fSocketTable i = 1 fd = 7
Jack: fSocketTable i = 2 fd = 10
Jack: fPollTable i = 1 fd = 7
Jack: fPollTable i = 2 fd = 10
Jack: JackRequest::ClientCheck
Jack: Check protocol client 8 server = 8
Jack: fPollTable i = 1 fd = 7
Jack: fPollTable i = 2 fd = 10
Jack: JackRequest::ClientOpen
Jack: JackSocketServerChannel::ClientAdd
Jack: JackEngine::ClientExternalOpen: name = qjackctl 
Jack: JackEngine::AllocateRefNum ref = 2
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_qjackctl val = 0
Jack: JackSocketNotifyChannel::Open name = qjackctl
Jack: Connect: addr.sun_path /dev/shm/jack_qjackctl_1000_0
Jack: JackShmMem::new index = 2 attached = b772b000 size = 120 
Jack: JackExternalClient::Open name = qjackctl index = 2 base = b772b000
Jack: JackProcessSync::TimedWait time out = 5000000
Jack: JackProcessSync::TimedWait finished delta = 20409.0
Jack: JackEngine::NotifyAddClient: name = qjackctl
Jack: JackExternalClient::ClientNotify ref = 0 name = system notify = 0
Jack: JackExternalClient::ClientNotify ref = 1 name = freewheel notify = 0
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 0
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 0
Jack: JackSocketServerChannel::BuildPoolTable size = 3
Jack: fSocketTable i = 1 fd = 7
Jack: fSocketTable i = 2 fd = 10
Cannot lock down memory area (Cannot allocate memory)
Jack: JackClient::SetupDriverSync driver sem in flush mode
Jack: JackPosixSemaphore::Connect jack_sem.1000_default_qjackctl
Jack: Already connected name = qjackctl
Jack: Clock source : system clock via clock_gettime
Jack: JackLibClient::Open name = qjackctl refnum = 2
Jack: jack_set_graph_order_callback ext_client 8d9a5c0 client 8d9a5c0 
Jack: SetGraphOrderCallback 
Jack: JackClient::Activate
Jack: fPollTable i = 1 fd = 7
Jack: fPollTable i = 2 fd = 10
Jack: JackRequest::ActivateClient
Jack: JackEngine::ClientActivate ref = 2 name = qjackctl
Jack: JackProcessSync::TimedWait time out = 464380
Jack: JackProcessSync::TimedWait finished delta = 12024.0
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 2
Jack: JackClient::kActivateClient name = qjackctl ref = 2 
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 4
Jack: JackEngine::NotifyClient: no callback for event = 4
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 4
Jack: JackClient::kGraphOrderCallback
Jack: fPollTable i = 2 fd = 10
Jack: WaitGraphChange...
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 4
Jack: JackEngine::NotifyClient: no callback for event = 4
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 4
Jack: fPollTable i = 2 fd = 10
Jack: JackClient::kGraphOrderCallback
Jack: fPollTable i = 1 fd = 7
Jack: fPollTable i = 2 fd = 10

Then these last two lines repeat while it is running.

---

### Post by cchhrriiss121212 on 2011-02-03
Could you post the whole output? Wrap it in code tags so that it won't take up the whole page.

---

### Post by setsuna on 2011-08-17
Hi, cchhrriiss121212

i've a same question with tman69..

but when i try step til alsamixer in terminal and press F6 to switch to USB sound card (same type as tman69) the capture option is not exist..

it said:
> This sound device does not have any capture controls. 

it show just PCM..

thx u so much :)

---

### Post by Segofam on 2011-11-01
Clearly time has past but...so I tried this:

[http://youtu.be/BR2qjFfYOU0](http://youtu.be/BR2qjFfYOU0)

Is that of any help to you!?

---

