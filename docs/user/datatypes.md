# Datatypes

As you learned in [Getting Started](/docs/user/started/#brainlifeio-terms-to-know), brainlife.io Apps exchange data through `datatypes`. We are now going to cover datatypes in-depth in this section -- you can check out all of the brainlife.io [datatypes here](https://brainlife.io/datatypes/){target=_blank}.

The screenshot below shows you a datatype. Each datatype consists of a `name`, `description`, and a list of `files` that define the datatype's structure.

![datatype](../img/datatypes.png)

The example below shows the datatype definition for the [neuro/life datatype](https://brainlife.io/datatype/58d15eaee13a50849b258844){target=_blank}

```json
{
    "name" : "neuro/life",
    "desc" : "LiFE Output (fe structure)",
    "files" : [
        {
            "id" : "fe",
            "filename" : "output_fe.mat",
            "desc" : "FE structure",
            "ext" : ".mat",
            "required" : true
        },
        {
            "id" : "life_results",
            "filename" : "life_results.json",
            "required" : true
        },
        {
            "id" : "tracts",
            "dirname" : "tracts",
            "required" : true
        }
    ]
}
```

In this example, the [brainlife/app-life](https://brainlife.io/app/5baa44b1d0be8b002776b8f7){target=_blank} App generates a data object with this datatype. Other Apps that want to use the `neuro/life` output can request to have the files made available to their Apps with the brainlife.io [App registration form](https://brainlife.io/docs/apps/register/).

It is important to note that it is up to the App developers to decide which datatype to use to exchange data between 2 Apps. An App developers can discuss the structure of the datatype and what each file means in the `#datatype` channel of [brainlife.io's Slack workspace](https://brainlife-inviter.herokuapp.com/){target=_blank}.

_Quick Note:_ While a datatype might sound similar to a [BIDS specification](https://bids-specification.readthedocs.io/en/stable/){target=_blank}, brainlife.io datatypes differ in that they:

* Mainly concern data derivatives generated by Apps and are used only by Apps exchanging those data objects.

* Are only used within the brainlife.io platform and are not meant to become standards for a particular data format

* Are defined by App developers involved in exchanging input/output data objects, not by brainlife.io platform developers

## Datatype Tags

Sometimes you want to be more specific about a particular datatype. For example, [neuro/anat/t1w](https://brainlife.io/datatype/58c33bcee13a50849b25879a){target=_blank} could be ACPC aligned or not and [neuro/dwi](https://brainlife.io/datatype/58c33c5fe13a50849b25879b){target=_blank} could be single-shell or multi-shell. brainlife.io allows you to specify each datatype with **datatype tags**.

You should only use datatype tag to be add more specificity, not generalize it. For example, we don't have "multi-shell" datatype tags because `neuro/dwi` is by default "multi-shell" data. While it is normal to have different b-values in a `dwi.bvals` file, "single-shell" is a special case for the `neuro/dwi` datatype where b-values happens to all be the same number -- so we added the "single-shell" tag to describe it.

Since datatype tags add specificity, brainlife.io can correctly identify which data object can be used for which Apps by examining datatype tags and an App's input datatype tags. But do not confuse a *datatype* tag with *data object* tag!

* A *datatype* tag can only be set by the App developer. It is part of the datatype and should not be modified once the object is created (user can still change it via the data object dialog box).

* A *data object* tag, on the other hand, is a tag that can be freely edited by any user, and it allows for easier searching or bulk processing.

!!! hint
    If you ever have any questions about datatypes, just ask them in the `#datatype` channel in [brainlife.io's Slack](https://brainlife-inviter.herokuapp.com/){target=_blank}!

## Visualization Tools

brainlife provides access to variety of visualization tools that can launched directly from user's web browser. Each tools are registered for specific datatype.

![vis tools](../img/vistools.png)

If you'd like to add a new visualization tool, you can contact the brainlife team to have it added to specific datatype.

We have developed the following custom visualization tools for brainlife.io

### TractView

[demo](https://brainlife.io/ui/tractview/){target=_blank}

![img](//brainlife.io/images/ui-logos/tractview.png)

### 3D Surfaces Viewer

[demo](https://brainlife.io/ui/surfaces/){target=_blank}

![img](https://brainlife.io/images/ui-logos/surfaces.png)

### NetworkNeuro Viewer

[demo](https://brainlife.io/ui/nnview/){target=_blank}

![img](https://brainlife.io/images/ui-logos/nnview.png)

### pRF Viwer

[demo](https://brainlife.io/ui/prfview/){target=_blank}


