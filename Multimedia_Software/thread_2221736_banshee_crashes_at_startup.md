---
title: "banshee crashes at startup"
date: 2014-05-03
forum: Multimedia Software
---

### Post by linuxgrrl on 2014-05-03
Hello,
Banshee crashes when I run it, but I am getting a different error than the others who posted the problem last year.

Here's what I get:

```
	/usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0(gst_plugin_load_file+0x285) [0x7fe908922885]
	/usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0(gst_plugin_load_by_name+0xa3) [0x7fe908923693]
	/usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0(gst_plugin_feature_load+0xce) [0x7fe90892405e]
	/usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0(gst_element_factory_create+0x2c) [0x7fe908900ddc]
	/usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0(gst_element_factory_make+0xef) [0x7fe90890117f]
	/usr/lib/banshee/libbanshee.so(_bp_pipeline_construct+0x208) [0x7fe909033a38]
	[0x4119ca14]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
No threads.

```

Any ideas?

---

