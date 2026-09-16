此包解决的问题：
（1）WorldLabs官网推出的将Marble worlds into Unity的包，不支持团结引擎，只支持Unity6以后的版本。
（2）使用官方包旧版本时，当将Marble worlds into 团结引擎后，出现资源PLY顶点大小不匹配的问题。
为此，我在官网包的基础上进行了改进，提出了将Marble worlds into 团结引擎的包，即Import Marble worlds into Unity using GaussianSplatting-Tuanjie plugins。
The only platforms where this is known to work are the ones that use D3D12, Metal or Vulkan graphics APIs. PC (Windows on D3D12 or Vulkan), Mac (Metal), Linux (Vulkan) should work. Anything else I have not actually tested; it might work or it might not.

Usage：
（1）Download or clone this repository, 然后将包解压后，放到你的团结项目的包里面，团结引擎会自动记载，并在工具中显示该包的功能；
（2）Note that the project requires DX12 or Vulkan on Windows, i.e. DX11 will not work.  First, ensure your project is using a supported Graphics API. For Windows: in Edit > Project Settings > Player > Other Settings, uncheck Auto Graphics API for Windows. Then, in the Graphics APIs for Windows list, add Vulkan or Direct3D12 and remove any other options. 

The next steps depend on the Render Pipeline you are using:

BiRP: Does not need any extra setup.
URP: Add Gsplat URP Feature to the URP renderer settings.
Find the Universal Renderer Data your project is using, click the Add Renderer Feature button, and choose Gsplat URP Feature.
If you are using Unity 6 or later, the Render Graph "Compatibility Mode" in URP settings must be turned off!
特别提醒：项目 Assets 目录下没有名为 "Universal Renderer Data" 的资产，但有 3 个 URP Renderer 资产在 Assets/Settings/ 下：
URP-Balanced-Renderer.asset
URP-HighFidelity-Renderer.asset （亲测结果：在这个下面添加才有效。）
URP-Performant-Renderer.asset
这些都是 URP 的 Universal Renderer Data，只是用了不同的命名。它们在 Assets/Settings/ 目录中。
HDRP: Add Custom Pass volume object in your scene and a Gsplat HDRP Pass entry to it. The injection Point should be set to Before Transparent.
（3）Next up, create some GaussianSplat assets: open Tools -> Gaussian Splats -> Create GaussianSplatAsset menu within Unity. In the dialog, point Input PLY/SPZ File to your Gaussian Splat file. 


