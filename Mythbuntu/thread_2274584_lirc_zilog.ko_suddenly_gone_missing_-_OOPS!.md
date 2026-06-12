---
title: "lirc_zilog.ko suddenly gone missing - OOPS!"
date: 2015-04-20
forum: Mythbuntu
---

### Post by jack35 on 2015-04-20
This weekend I did a fresh install of Mythbuntu 14.04.2. After a few small problems (missing HD_PVR firmware) the system was up and running well.

Then I did an update to kernel 3.16.0-34 and everything seemed to still be okay. Today I try to watch the HD Pvr and it won't tune to the channel. I found that lirc_zilog.ko is missing. There is a lirc_zilog.ko in the staging area (that won't load) but not in the normal directory. 

Anyone have any ideas? where can I get a working copy?

Thanks,

Jack

To add some clarification:
```

user@htpc1:~$ find /lib/modules/`uname -r`/kernel/drivers -name "lirc*"
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc/lirc_bt829.ko
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc/lirc_parallel.ko
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc/lirc_serial.ko
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc/lirc_imon.ko
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc/lirc_sir.ko
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc/lirc_igorplugusb.ko
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc/lirc_zilog.ko
/lib/modules/3.16.0-34-generic/kernel/drivers/staging/media/lirc/lirc_sasem.ko
/lib/modules/3.16.0-34-generic/kernel/drivers/media/rc/lirc_dev.ko
user@htpc1:~$

```

There are no drivers in drivers/media/rc they are all in drivers/staging/media/lirc. Trying to copy the needed driver into drivers/media/rc doesn't work. So I guess the real question now is does linux still support the HD-PVR ir blaster? And maybe this should be posted in the Ubuntu form?

Thanks,

Jack

Okay... So all the above is babble...

The kernel modules are where the belong. In  3.16.0-34-generic I get the following:
> 
Apr 24 10:58:02 htpc1 kernel: [   14.579696] lirc_zilog: module is from the staging directory, the quality is unknown, you have been warned.
Apr 24 10:58:02 htpc1 kernel: [   14.579761] lirc_zilog: Unknown symbol lirc_unregister_driver (err 0)
Apr 24 10:58:02 htpc1 kernel: [   14.579786] lirc_zilog: Unknown symbol lirc_register_driver (err 0)


In the previous version 3.16.0-30-generic I get:
> 
Apr 19 18:18:07 htpc1 kernel: [ 5616.705539] lirc_zilog: module is from the staging directory, the quality is unknown, you have been warned.
Apr 19 18:18:07 htpc1 kernel: [ 5616.705882] lirc_zilog: Zilog/Hauppauge IR driver initializing
Apr 19 18:18:07 htpc1 kernel: [ 5616.709072] lirc_zilog: probing IR Rx on Hauppage HD PVR I2C (i2c-0)
Apr 19 18:18:07 htpc1 kernel: [ 5616.709251] lirc_zilog: probe of IR Rx on Hauppage HD PVR I2C (i2c-0) done. Waiting on IR Tx.
Apr 19 18:18:07 htpc1 kernel: [ 5616.709261] lirc_zilog: probe of IR Rx on Hauppage HD PVR I2C (i2c-0) done
Apr 19 18:18:07 htpc1 kernel: [ 5616.709301] lirc_zilog: probing IR Tx on Hauppage HD PVR I2C (i2c-0)
Apr 19 18:18:07 htpc1 kernel: [ 5616.709363] i2c i2c-0: Direct firmware load failed with error -2
Apr 19 18:18:07 htpc1 kernel: [ 5616.709368] i2c i2c-0: Falling back to user helper
Apr 19 18:18:07 htpc1 kernel: [ 5616.710519] lirc_zilog: firmware haup-ir-blaster.bin not available (-12)
Apr 19 18:18:07 htpc1 kernel: [ 5616.710802] i2c i2c-0: lirc_dev: driver lirc_zilog registered at minor = 0
Apr 19 18:18:07 htpc1 kernel: [ 5616.710808] lirc_zilog: IR unit on Hauppage HD PVR I2C (i2c-0) registered as lirc0 and ready
Apr 19 18:18:07 htpc1 kernel: [ 5616.710811] lirc_zilog: probe of IR Tx on Hauppage HD PVR I2C (i2c-0) done
Apr 19 18:18:07 htpc1 kernel: [ 5616.710851] lirc_zilog: initialization complete


This shows the missing firmware error. I did get that fixed and everything worked. So it looks like either lirc_dev.ko or lirc_zilog.ko have a problem in 34.

Jack

---

