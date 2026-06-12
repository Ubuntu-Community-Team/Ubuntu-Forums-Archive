---
title: "Hugin does not start anymore"
date: 2017-07-19
forum: Multimedia Software
---

### Post by Roland_Msl on 2017-07-19
Hugin does not start anymore - would be nice, if it would be possible to edit also the title (solved)

I have Ubuntu 16.04 LTE

I installed and tested Hugin one year ago. Everything worked.

Now I get an ERROR at starting and Hugin terminates.

I removed and installed again, no effect

---

### Post by monkeybrain20122 on 2017-07-19
Which version is that? Maybe upgrading with its ppa will fix it. [https://launchpad.net/~hugin/+archive/ubuntu/hugin-builds](https://launchpad.net/~hugin/+archive/ubuntu/hugin-builds)

---

### Post by mc4man on 2017-07-19
> **Roland_Msl said:**
>  would be nice, if it would be possible to edit also the subject

Go back to the 1st. post > Edit Post  > Go Advanced > change the Title: as you wish

---

### Post by Roland_Msl on 2017-07-20
> **monkeybrain20122 said:**
> Which version is that? Maybe upgrading with its ppa will fix it. [https://launchpad.net/~hugin/+archive/ubuntu/hugin-builds](https://launchpad.net/~hugin/+archive/ubuntu/hugin-builds)

It's the version which installs with Ubuntu Software

Just tried this with Your link.
But the same 

ASSERT INFO:
/usr/include/wx-3.0/wx/object.h(160): assert "wxDynamicCast(ptr, T)" failed in wxCheckCast(): wxStaticCast() used incorrectly


BACKTRACE:
[1] GLPreviewFrame::SetGuiLevel(GuiLevel)
[2] MainFrame::SetGuiLevel(GuiLevel)
[3] MainFrame::MainFrame(wxWindow*, HuginBase::Panorama&)
[4] huginApp::OnInit()
[5] wxEntry(int&, wchar_t**)
[6] main
[7] __libc_start_main
[8] _start


and crashes just after the error box is closed

---

### Post by Roland_Msl on 2017-07-20
Just tested on an other Acer ES1-331-C0YK where I installed Ubuntu 16.04 LTS with the same USB Stick.
Installation worked.
Loaded 4 pictures - started align - found 125 control points, box came "Align failed".

BTW, I have now for all the family 4 Acer ES1-331 series.

---

### Post by Roland_Msl on 2017-07-20
Just found out what was the problem. I brought the picture on a Micro-SD card to the other notebook.
Seems the align part does not like to write on FAT 32.
Copied all to the personal folder, here it works.

Only strange, that on my notebook, Hugin crashes.

---

