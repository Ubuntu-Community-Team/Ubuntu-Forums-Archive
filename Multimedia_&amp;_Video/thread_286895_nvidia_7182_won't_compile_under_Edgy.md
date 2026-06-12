---
title: "nvidia 7182 won't compile under Edgy"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by oblib on 2006-10-28
For whatever reason, I've always had to use the 7182 driver for my nVidia Corporation NV17 [GeForce4 MX 440] (rev a3). However, when I went to compile it on Edgy, I got a couple of compile errors:
```
usr/src/nv/nv-linux.h:667: error: conflicting types for 'pm_message_t'
```That error comes from this code:```
#if defined(KERNEL_2_6) && !defined(NV_PM_MESSAGE_T_PRESENT)
typedef u32 pm_message_t;
#endif
```So it seems as if the new kernel is not reporting that PM_MESSAGE is present. So I commented out the typedef and got this error:
```
usr/src/nv/nv.c:4109: error: incompatible types in assignment
```Which is this:```
#if !defined(NV_PM_MESSAGE_T_PRESENT)
    power_state = state;
#elsif defined(NV_PCI_CHOOSE_STATE_PRESENT)
    power_state = pci_choose_state(dev, state);
#endif
```So, same problem here. I changed it so that it only iffed on the NV_PCI... and got the next and last error:```
usr/src/nv/os-interface.c:1224: error: 'struct task_struct' has no member named 'rlim'
```This one I don't understand as well. The code section is this:```
    /*
     * The NVIDIA driver may require the ability to lock down user
     * memory with the mlock(2) system call, which is normally only
     * available to privileged processes. The code below enables
     * mlock(2) for the current process and adjusts the lock limit
     * to 'unlimited'.
     *
     * If you prefer to manually grant the necessary capability and
     * adjust the resource limit, disable the lines below.
     */
#if 1 /* enabled */
    struct rlimit *rlim = NV_TASK_STRUCT_RLIM(current);
    rlim[RLIMIT_MEMLOCK].rlim_cur = RLIM_INFINITY;
    cap_raise(current->cap_effective, CAP_IPC_LOCK);
    return RM_OK;
#endif
    return RM_ERROR;
```
If I change that '#if 1' to '#if 0' then it compiles without anymore warnings. But if I do that, what are the consequences? I am not manually granting "the necessary capability" so is something not going to work?

In any case when I installed it, I couldn't get OpenGL to work (I think I deleted a file out of /usr/lib that I shouldn't have) and I have been working on getting a package to work. Status right now: I have nvidia-glx installed and just get a black screen and an error in Xorg.log that it can't load the kernel module nvidia. I have followed all the guides I could find (especially tseliot's).

---

