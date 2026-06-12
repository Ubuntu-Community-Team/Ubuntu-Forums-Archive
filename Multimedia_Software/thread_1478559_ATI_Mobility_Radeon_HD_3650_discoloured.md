---
title: "ATI Mobility Radeon HD 3650 discoloured"
date: 2010-05-09
forum: Multimedia Software
---

### Post by rcmn on 2010-05-09
Card on my Lenovo W500. ATI Technologies Inc Mobility Radeon HD 3650

I had kubuntu installed for 1.5/2 years now. I keep upgrading when a new release is in beta. So I did the same with 10.4. But right away I started to have some strange video issues. Randomly my screen will become partially or entirely discoloured.(Sort of melting effect until it become more or less white). Enabling a new screen using the "F" keys will not fix the issue. Only a restart X will clear the defect. 
So today I decided to completely reinstall. I was surprise to see my install window waiting for a reboot with half of the screen discoloured again. So I guess the issue is not solved. 
I search the forum but I must use the wrong keywords .Anyone have heard of that or seen a post talking about a similar problem.THX

some info:
> modinfo radeon
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
license:        GPL and additional rights
description:    ATI Radeon
author:         Gareth Hughes, Keith Whitwell, others.

depends:        drm,drm_kms_helper,ttm,i2c-algo-bit
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           no_wb:Disable AGP writeback for scratch registers (int)
parm:           modeset:Disable/Enable modesetting (int)
parm:           dynclks:Disable/Enable dynamic clocks (int)
parm:           r4xx_atom:Enable ATOMBIOS modesetting for R4xx (int)
parm:           vramlimit:Restrict VRAM for testing (int)
parm:           agpmode:AGP Mode (-1 == PCI) (int)
parm:           gartsize:Size of PCIE/IGP gart to setup in megabytes (32,64, etc)
 (int)
parm:           benchmark:Run benchmark (int)
parm:           test:Run tests (int)
parm:           connector_table:Force connector table (int)
parm:           tv:TV enable (0 = disable) (int)
parm:           new_pll:Select new PLL code (int)
parm:           audio:Audio enable (0 = disable) (int)

---

