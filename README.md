# Transfer-Prompts-for-Text-Generation

This is the repository for NAACL 2022 paper "Learning to Transfer Prompts for Text Generation". The implementation is completely based on our newly-developed text generation library **[TextBox 2.0](https://github.com/RUCAIBox/TextBox)**

## Prompt Source
The `prompt_source.pth` in this repository contains the source task prompts (*i.e.*, tensors of shape `[200,1024]`) trained on 14 datasets as introduced in our paper:
- CNN/Daily Mail (cmmdn)
- XSum (xsum)
- MSNews (msn)
- Multi-News (mn)
- NEWSROOM (nr)
- SQuAD (squad)
- Wiki Neutrality (wiki)
- Quora (quora)
- PersonaChat (pc)
- DailyDialog (dd)
- DSTC7-AVSD (da)
- MultiWOZ (mw)
- WritingPrompts (wp)

You can also download these datasets [here](https://github.com/RUCAIBox/TextBox#dataset).

## Installation
First, you should clone the TextBox repository and follow its [instructions](https://github.com/RUCAIBox/TextBox#installation).

Then, you may copy the `prompt_source.pth` into the TextBox folder.

## Running PTG based on TextBox
For example, you can conduct our cross-dataset experiments on cnndm dataset using this command:
```bash
python run_textbox.py --model=PTG --dataset=cnndm --model_path=facebook/bart-large
```
In this default case, the source tasks (datasets) is msn, mn, and nr.

You can use `--dataset=xxx` to specify the dataset name.

In addition, you can also specify the source tasks using `--source_task=list_of_task`. The default setting is equivalent to `--source_task=\[\'msn\',\'mn\',\'nr\'\]`.

We also provide several cases used in our paper:
- `--source_task=cross-dataset2`: tc, da, mw.
- `--source_task=cross-task1`: squad, wiki, quora, wp, cnndm.
- `--source_task=cross-task2`: squad, wiki, quora, wp, pc.



## Reference
```bibtex
@inproceedings{li-etal-2022-learning-transfer,
    title = "Learning to Transfer Prompts for Text Generation",
    author = "Li, Junyi  and
      Tang, Tianyi  and
      Nie, Jian-Yun  and
      Wen, Ji-Rong  and
      Zhao, Xin",
    booktitle = "Proceedings of the 2022 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies",
    month = jul,
    year = "2022",
    address = "Seattle, United States",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.naacl-main.257",
    doi = "10.18653/v1/2022.naacl-main.257",
    pages = "3506--3518",
}
```
