---
title: "CPU always busy"
date: 2020-02-11
forum: MINT
---

### Post by tonygraziano on 2020-02-11
Hi there, 

I have a Toshiba Protege with Mint 19.3 and have kdenlive image installed. When I work with kdenlive the CPU works at the maximum and the system slown down dramatically. It almost happenes also when I just have Internet browser opened. 

A few months ago on the same PC I had mint 17 installed and it did not give these troubles, even with the same programmes. 

My CPU is
[COLOR=#101010][FONT=Ubuntu]Dual Core Intel Core i5-3427U (-MT MCP-)[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]speed/min/max: 903/800/2800 MHz Kernel: 5.3.0-26-generic x86_64 Up: 5h 35m[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Mem: 3556.8/5823.6 MiB (61.1%) Storage: 119.24 GiB (61.7% used) Procs: 240[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Shell: bash 4.4.20 inxi: 3.0.32

Tahank you so much for your help[/FONT][/COLOR]

---

### Post by jeremy31 on 2020-02-11
Moved to Mint

---

### Post by thehipho on 2020-02-11
> 
A few months ago on the same PC I had mint 17 installed and it did not give these troubles, even with the same programmes. 


Hi, welcome to the forum!

It's really hard to compare versions of Os's and their related different versions of software, changes may not always be compatible with your install. 

And anything CPU intensive needs lots ram and fast graphics!

Post output of:
```
glxinfo | grep render

```

---

### Post by tonygraziano on 2020-02-12
> **thehipho said:**
> Hi, welcome to the forum!

It's really hard to compare versions of Os's and their related different versions of software, changes may not always be compatible with your install. 

And anything CPU intensive needs lots ram and fast graphics!

Post output of:
```
glxinfo | grep render

```
HI thank you

This is the output
```
anto@anto-PORTEGE-Z930:~$ glxinfo | grep render
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_query_renderer, GLX_MESA_swap_control, GLX_OML_swap_method, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
    GL_ARB_compute_shader, GL_ARB_conditional_render_inverted, 
    GL_NV_compute_shader_derivatives, GL_NV_conditional_render, 
    GL_ARB_compute_shader, GL_ARB_conditional_render_inverted, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fog_distance, 
    GL_MESA_shader_integer_functions, GL_NV_conditional_render, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap,
```

---

### Post by thehipho on 2020-02-12
I recommend adding more ram if possible (8Gb), should make a big difference for old laptops to run newer Os's.

---

### Post by tonygraziano on 2020-02-13
> **thehipho said:**
> I recommend adding more ram if possible (8Gb), should make a big difference for old laptops to run newer Os's.
Thank you!

---

