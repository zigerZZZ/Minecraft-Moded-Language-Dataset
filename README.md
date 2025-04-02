# 仓库说明

这是一个整合了Minecraft模组、整合包以及原版数据的语言文件的数据集仓库，用于AI训练。

**仓库未对任何特殊符号做预处理，仅仅只是整合！**

对于翻译文本，提供三项数据：`key`,`src`,`target`，分别表示：`游戏内的键`,`原文`,`译文`

# 训练数据与测试数据

提供共计`522046`条平行预料，其中`test.csv`包含`10000`条数据，`train.csv`包含`512046`条数据。
已针对数据进行去重/删除空值处理，原始数据`70w+`

# 数据来源

`modpack/tmp`文件夹下提供了来自[VM汉化组](https://vmct-cn.top/)的所有包含ftbquests语言文件的整合包文件。

`projects`文件夹来自CFPA的[Minecraft-Mod-Language-Package](https://github.com/CFPAOrg/Minecraft-Mod-Language-Package)的同名文件夹，包含绝大多数Minecraft模组的中英对照。

`wiki.html`文件来自[Minecraft Wiki:译名标准化](https://zh.minecraft.wiki/w/Minecraft_Wiki:%E8%AF%91%E5%90%8D%E6%A0%87%E5%87%86%E5%8C%96),几乎所有的中英对照都在其中。

*原版数据并没有划分到测试集中*

# 数据整合

**要扩展数据集，可以参考这里**

## modpack 文件夹

该文件夹下包含了`generate_dataset.py`，请在`Minecraft-Mod-Language-Package/modpack/`目录下运行。该文件来自XDawned/[minecraft-quests-en-zh](https://github.com/XDawned/minecraft-quests-en-zh)`data`目录下的同名文件。生成中英对照预料，请参考：

  1. 获取包含ftbquests任务文件的整合包的覆盖文件(*也就是在curseforge上下载到的原包*)，和汉化包
  2. 分别找到两个包中的`config/ftbquests`并分别命名为`ftbquests-en`,`ftbquests-zh`，移动到`modpack/tmp/整包名称/`文件夹下
  3. 运行`generate_dataset.py`，对每个包下的`zh_en.csv`做合并即可。

## projects 文件夹 

该文件夹下是[Minecraft-Mod-Language-Package](https://github.com/CFPAOrg/Minecraft-Mod-Language-Package)资源包的语言文件对照；针对每个子文件夹，寻找所有的`en_us.json`,`en_us.lang`；并查找同级目录下的中文语言文件，形成对照。若有相同类似数据，可以在该目录下新建子文件夹，并参考`data_process.ipynb`进行处理。

处理后的数据会存到patched目录下。

