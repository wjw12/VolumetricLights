# Volumetric Lights for Unity 5

The original project can be found [here](https://github.com/SlightlyMad/VolumetricLights). And the following is a brief introduction by the original author:

[![IMAGE ALT TEXT HERE](https://bqu2ya.dm1.livefilestore.com/y4mSxIn4D7Zx9td_2NWn3yZu8UxWeqJKN4qdciZ0fCqO9ox290xR837Moux6HnPpWPkF8mi7oY26ZNF7n0eJfbPMNoBTtrMraKnghJ4XF13tCK2bBPybZVudlL1UU_gBkFyY7lt30UYbVJ-EZVaV2Z8C1DglijmBYelQfJyplssFe7oSklBvneGtDlhwDv1dougv2ZpHmipfzYRuR6fLeawlQ?width=1167&height=653&cropmode=none)](https://www.youtube.com/watch?v=JPxLCYXB-8A) [![IMAGE ALT TEXT HERE](https://agu0ya-dm2305.files.1drv.com/y4mnqQ4pzhZdF4k3Z7Fv_QApimv9POLR1ShQPoNg8wtUf7TzqFdWLY6Y8bxtyJhGQNRe8NLvy1GGoZsorNssr2h6fTsAfyi-F2LOIA4wzNY_7cS-1iEjVHyOCyOCTA0_8na3cmWvQ34gHBfyXOxxE6AZIjaVwCemZP7kSwaUNoNDyCPsCkx8vsdmxuwmuVcrH1rYblmFCaVH5za_EsrqM-qJA?width=1167&height=650&cropmode=none)](https://www.youtube.com/watch?v=ElaPJyzR504)

Open source (BSD) extension for built-in Unity lights. It uses ray marching in light's volume to compute volumetric fog. This technique is similar to the one used in Killzone ([GPU Pro 5](http://www.amazon.com/GPU-Pro-Advanced-Rendering-Techniques/dp/1482208636): Volumetric Light Effects in Killzone Shadow Fall by Nathan Vos)

Corresponding thread in Unity Forum can be found [here](http://forum.unity3d.com/threads/true-volumetric-lights-open-source-soon.390818/).

### Multichromatic Light Extension

I added a few lines of code, namely creating new script VolumetricLightProjector.cs and new shader VolumetricProjection.shader so that the light volume can be multichromatic, which resulted in:

[![IMAGE ALT TEXT HERE](http://wjwtest.oss-cn-qingdao.aliyuncs.com/cg_exercise/02/v2.jpg)]

The following gif is rendered with the camera lying inside the light volume and the spotlight is rotating along its local axis.

[![IMAGE ALT TEXT HERE](http://wjwtest.oss-cn-qingdao.aliyuncs.com/cg_exercise/02/1.gif)]

To use this multichromatic light volume, attach VolumetricLightProjector.cs instead of VolumetricLight.cs to the lights that you want to create this effect on. And then add a colored image as light projection texture. 

The idea of my algorithm is: When performing raymarching in light's volume, we sample the color from light projection texture. Color are accumulated on the way to achieve the final output color.