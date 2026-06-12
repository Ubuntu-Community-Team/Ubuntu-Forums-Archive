---
title: "V4L Build Issues"
date: 2011-04-13
forum: Multimedia Software
---

### Post by demahac on 2011-04-13
I'm trying to get v4l to work by using the following steps:

git clone git://linuxtv.org/media_build.git cd media_build  ./build.sh 
[FONT=Verdana]
[/FONT][FONT=Arial]However, when trying to do the final step i get the following error:

 CC [M]  /home/nikhil/media_build/v4l/timblogiw.o
/home/nikhil/media_build/v4l/timblogiw.c: In function 'timblogiw_probe':
/home/nikhil/media_build/v4l/timblogiw.c:794: error: implicit declaration of function 'mfd_get_data'
/home/nikhil/media_build/v4l/timblogiw.c:794: warning: initialization makes pointer from integer without a cast
make[3]: *** [/home/nikhil/media_build/v4l/timblogiw.o] Error 1
make[2]: *** [_module_/home/nikhil/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/nikhil/media_build/v4l'
make: *** [all] Error 2
*** ERROR. Aborting ***

I think the relevant region of the timblogiw.c file is:
[/FONT]```
static int __devinit timblogiw_probe(struct platform_device *pdev)
{
    int err;
    struct timblogiw *lw = NULL;
    struct timb_video_platform_data *pdata = mfd_get_data(pdev);

    if (!pdata) {
        dev_err(&pdev->dev, "No platform data\n");
        err = -EINVAL;
        goto err;
    }

    if (!pdata->encoder.module_name)
        dev_info(&pdev->dev, "Running without decoder\n");

    lw = kzalloc(sizeof(*lw), GFP_KERNEL);
    if (!lw) {
        err = -ENOMEM;
        goto err;
    }

    if (pdev->dev.parent)
        lw->dev = pdev->dev.parent;
    else
        lw->dev = &pdev->dev;

    memcpy(&lw->pdata, pdata, sizeof(lw->pdata));

    mutex_init(&lw->lock);

    lw->video_dev = timblogiw_template;

    strlcpy(lw->v4l2_dev.name, DRIVER_NAME, sizeof(lw->v4l2_dev.name));
    err = v4l2_device_register(NULL, &lw->v4l2_dev);
    if (err)
        goto err_register;

    lw->video_dev.v4l2_dev = &lw->v4l2_dev;

    platform_set_drvdata(pdev, lw);
    video_set_drvdata(&lw->video_dev, lw);

    err = video_register_device(&lw->video_dev, VFL_TYPE_GRABBER, 0);
    if (err) {
        dev_err(&pdev->dev, "Error reg video: %d\n", err);
        goto err_request;
    }


    return 0;

err_request:
    platform_set_drvdata(pdev, NULL);
    v4l2_device_unregister(&lw->v4l2_dev);
err_register:
    kfree(lw);
err:
    dev_err(&pdev->dev, "Failed to register: %d\n", err);

    return err;
}
```[FONT=Arial]

And i think its a missing header file (mfd_get_data) but i can't seem to find where to get it.



[/FONT]

---

### Post by wolfen69 on 2011-04-13
You can get the latest v4l by adding a ppa to your sources list then downloading it normally via synaptic. Much easier plus you will get updates. [https://launchpad.net/~libv4l/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~libv4l/+archive/ppa?field.series_filter=maverick)

I assumed you are using ubuntu 10.10

---

### Post by Akriss on 2011-04-16
However, 

If you really need to build it by hand. You can open .config file in the  v4l directory with you text editor of choice and search for the line TIMBERDALE=m and change it to TIMBERDALE=n .

Then run make.

By doing that you are not building the timberdale portions.

---

### Post by Zeratul021 on 2011-04-19
Hey,

nice tip, thanks.

---

