.. only:: html

    .. note::
        :class: sphx-glr-download-link-note

        Click :ref:`here <sphx_glr_download_auto_examples_plot_simulate_alpha.py>`     to download the full example code or to run this example in your browser via Binder
    .. rst-class:: sphx-glr-example-title

    .. _sphx_glr_auto_examples_plot_simulate_alpha.py:


====================
Simulate alpha waves
====================

This example demonstrates how to simulate alpha waves using
HNN-core.


.. code-block:: default


    # Authors: Mainak Jas <mainak.jas@telecom-paristech.fr>
    #          Sam Neymotin <samnemo@gmail.com>

    import os.path as op








Let us import hnn_core


.. code-block:: default


    import hnn_core
    from hnn_core import simulate_dipole, read_params, Network








Then we setup the directories and Neuron


.. code-block:: default

    hnn_core_root = op.dirname(hnn_core.__file__)








Then we read the default parameters file


.. code-block:: default

    params_fname = op.join(hnn_core_root, 'param', 'default.json')
    params = read_params(params_fname)
    print(params)





.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none

    {
        "L2Basket_Gauss_A_weight": 0.0,
        "L2Basket_Gauss_mu": 2000.0,
        "L2Basket_Gauss_sigma": 3.6,
        "L2Basket_Pois_A_weight_ampa": 0.0,
        "L2Basket_Pois_A_weight_nmda": 0.0,
        "L2Basket_Pois_lamtha": 0.0,
        "L2Pyr_Gauss_A_weight": 0.0,
        "L2Pyr_Gauss_mu": 2000.0,
        "L2Pyr_Gauss_sigma": 3.6,
        "L2Pyr_Pois_A_weight_ampa": 0.0,
        "L2Pyr_Pois_A_weight_nmda": 0.0,
        "L2Pyr_Pois_lamtha": 0.0,
        "L2Pyr_ampa_e": 0.0,
        "L2Pyr_ampa_tau1": 0.5,
        "L2Pyr_ampa_tau2": 5.0,
        "L2Pyr_apical1_L": 306.0,
        "L2Pyr_apical1_diam": 4.08,
        "L2Pyr_apicaloblique_L": 340.0,
        "L2Pyr_apicaloblique_diam": 3.91,
        "L2Pyr_apicaltrunk_L": 59.5,
        "L2Pyr_apicaltrunk_diam": 4.25,
        "L2Pyr_apicaltuft_L": 238.0,
        "L2Pyr_apicaltuft_diam": 3.4,
        "L2Pyr_basal1_L": 85.0,
        "L2Pyr_basal1_diam": 4.25,
        "L2Pyr_basal2_L": 255.0,
        "L2Pyr_basal2_diam": 2.72,
        "L2Pyr_basal3_L": 255.0,
        "L2Pyr_basal3_diam": 2.72,
        "L2Pyr_dend_Ra": 200.0,
        "L2Pyr_dend_cm": 0.6195,
        "L2Pyr_dend_el_hh2": -65.0,
        "L2Pyr_dend_gbar_km": 250.0,
        "L2Pyr_dend_gkbar_hh2": 0.01,
        "L2Pyr_dend_gl_hh2": 4.26e-05,
        "L2Pyr_dend_gnabar_hh2": 0.15,
        "L2Pyr_gabaa_e": -80.0,
        "L2Pyr_gabaa_tau1": 0.5,
        "L2Pyr_gabaa_tau2": 5.0,
        "L2Pyr_gabab_e": -80.0,
        "L2Pyr_gabab_tau1": 1.0,
        "L2Pyr_gabab_tau2": 20.0,
        "L2Pyr_nmda_e": 0.0,
        "L2Pyr_nmda_tau1": 1.0,
        "L2Pyr_nmda_tau2": 20.0,
        "L2Pyr_soma_L": 22.1,
        "L2Pyr_soma_Ra": 200.0,
        "L2Pyr_soma_cm": 0.6195,
        "L2Pyr_soma_diam": 23.4,
        "L2Pyr_soma_el_hh2": -65.0,
        "L2Pyr_soma_gbar_km": 250.0,
        "L2Pyr_soma_gkbar_hh2": 0.01,
        "L2Pyr_soma_gl_hh2": 4.26e-05,
        "L2Pyr_soma_gnabar_hh2": 0.18,
        "L5Basket_Gauss_A_weight": 0.0,
        "L5Basket_Gauss_mu": 2000.0,
        "L5Basket_Gauss_sigma": 2.0,
        "L5Basket_Pois_A_weight_ampa": 0.0,
        "L5Basket_Pois_A_weight_nmda": 0.0,
        "L5Basket_Pois_lamtha": 0.0,
        "L5Pyr_Gauss_A_weight": 0.0,
        "L5Pyr_Gauss_mu": 2000.0,
        "L5Pyr_Gauss_sigma": 4.8,
        "L5Pyr_Pois_A_weight_ampa": 0.0,
        "L5Pyr_Pois_A_weight_nmda": 0.0,
        "L5Pyr_Pois_lamtha": 0.0,
        "L5Pyr_ampa_e": 0.0,
        "L5Pyr_ampa_tau1": 0.5,
        "L5Pyr_ampa_tau2": 5.0,
        "L5Pyr_apical1_L": 680.0,
        "L5Pyr_apical1_diam": 7.48,
        "L5Pyr_apical2_L": 680.0,
        "L5Pyr_apical2_diam": 4.93,
        "L5Pyr_apicaloblique_L": 255.0,
        "L5Pyr_apicaloblique_diam": 5.1,
        "L5Pyr_apicaltrunk_L": 102.0,
        "L5Pyr_apicaltrunk_diam": 10.2,
        "L5Pyr_apicaltuft_L": 425.0,
        "L5Pyr_apicaltuft_diam": 3.4,
        "L5Pyr_basal1_L": 85.0,
        "L5Pyr_basal1_diam": 6.8,
        "L5Pyr_basal2_L": 255.0,
        "L5Pyr_basal2_diam": 8.5,
        "L5Pyr_basal3_L": 255.0,
        "L5Pyr_basal3_diam": 8.5,
        "L5Pyr_dend_Ra": 200.0,
        "L5Pyr_dend_cm": 0.85,
        "L5Pyr_dend_el_hh2": -71.0,
        "L5Pyr_dend_gbar_ar": 1e-06,
        "L5Pyr_dend_gbar_ca": 60.0,
        "L5Pyr_dend_gbar_cat": 0.0002,
        "L5Pyr_dend_gbar_kca": 0.0002,
        "L5Pyr_dend_gbar_km": 200.0,
        "L5Pyr_dend_gkbar_hh2": 0.01,
        "L5Pyr_dend_gl_hh2": 4.26e-05,
        "L5Pyr_dend_gnabar_hh2": 0.14,
        "L5Pyr_dend_taur_cad": 20.0,
        "L5Pyr_gabaa_e": -80.0,
        "L5Pyr_gabaa_tau1": 0.5,
        "L5Pyr_gabaa_tau2": 5.0,
        "L5Pyr_gabab_e": -80.0,
        "L5Pyr_gabab_tau1": 1.0,
        "L5Pyr_gabab_tau2": 20.0,
        "L5Pyr_nmda_e": 0.0,
        "L5Pyr_nmda_tau1": 1.0,
        "L5Pyr_nmda_tau2": 20.0,
        "L5Pyr_soma_L": 39.0,
        "L5Pyr_soma_Ra": 200.0,
        "L5Pyr_soma_cm": 0.85,
        "L5Pyr_soma_diam": 28.9,
        "L5Pyr_soma_el_hh2": -65.0,
        "L5Pyr_soma_gbar_ar": 1e-06,
        "L5Pyr_soma_gbar_ca": 60.0,
        "L5Pyr_soma_gbar_cat": 0.0002,
        "L5Pyr_soma_gbar_kca": 0.0002,
        "L5Pyr_soma_gbar_km": 200.0,
        "L5Pyr_soma_gkbar_hh2": 0.01,
        "L5Pyr_soma_gl_hh2": 4.26e-05,
        "L5Pyr_soma_gnabar_hh2": 0.16,
        "L5Pyr_soma_taur_cad": 20.0,
        "N_pyr_x": 10,
        "N_pyr_y": 10,
        "N_trials": 1,
        "T_pois": -1,
        "celsius": 37.0,
        "dipole_scalefctr": 3000,
        "dipole_smooth_win": 30,
        "distribution_dist": "normal",
        "distribution_prox": "normal",
        "dt": 0.025,
        "dt_evprox0_evdist": -1,
        "dt_evprox0_evprox1": -1,
        "events_per_cycle_dist": 2,
        "events_per_cycle_prox": 2,
        "f_input_dist": 10.0,
        "f_input_prox": 10.0,
        "f_max_spec": 100,
        "f_stdev_dist": 20.0,
        "f_stdev_prox": 20.0,
        "gbar_L2Basket_L2Basket": 0.02,
        "gbar_L2Basket_L2Pyr_gabaa": 0.05,
        "gbar_L2Basket_L2Pyr_gabab": 0.05,
        "gbar_L2Basket_L5Pyr": 0.001,
        "gbar_L2Pyr_L2Basket": 0.0005,
        "gbar_L2Pyr_L2Pyr_ampa": 0.0005,
        "gbar_L2Pyr_L2Pyr_nmda": 0.0005,
        "gbar_L2Pyr_L5Basket": 0.00025,
        "gbar_L2Pyr_L5Pyr": 0.00025,
        "gbar_L5Basket_L5Basket": 0.02,
        "gbar_L5Basket_L5Pyr_gabaa": 0.025,
        "gbar_L5Basket_L5Pyr_gabab": 0.025,
        "gbar_L5Pyr_L5Basket": 0.0005,
        "gbar_L5Pyr_L5Pyr_ampa": 0.0005,
        "gbar_L5Pyr_L5Pyr_nmda": 0.0005,
        "gbar_evdist_1_L2Basket_ampa": 0.006562,
        "gbar_evdist_1_L2Basket_nmda": 0.019482,
        "gbar_evdist_1_L2Pyr_ampa": 7e-06,
        "gbar_evdist_1_L2Pyr_nmda": 0.004317,
        "gbar_evdist_1_L5Pyr_ampa": 0.1423,
        "gbar_evdist_1_L5Pyr_nmda": 0.080074,
        "gbar_evprox_1_L2Basket_ampa": 0.08831,
        "gbar_evprox_1_L2Basket_nmda": 0.0,
        "gbar_evprox_1_L2Pyr_ampa": 0.01525,
        "gbar_evprox_1_L2Pyr_nmda": 0.0,
        "gbar_evprox_1_L5Basket_ampa": 0.19934,
        "gbar_evprox_1_L5Basket_nmda": 0.0,
        "gbar_evprox_1_L5Pyr_ampa": 0.00865,
        "gbar_evprox_1_L5Pyr_nmda": 0.0,
        "gbar_evprox_2_L2Basket_ampa": 3e-06,
        "gbar_evprox_2_L2Basket_nmda": 0.0,
        "gbar_evprox_2_L2Pyr_ampa": 1.43884,
        "gbar_evprox_2_L2Pyr_nmda": 0.0,
        "gbar_evprox_2_L5Basket_ampa": 0.008958,
        "gbar_evprox_2_L5Basket_nmda": 0.0,
        "gbar_evprox_2_L5Pyr_ampa": 0.684013,
        "gbar_evprox_2_L5Pyr_nmda": 0.0,
        "inc_evinput": 0.0,
        "input_dist_A_delay_L2": 5.0,
        "input_dist_A_delay_L5": 5.0,
        "input_dist_A_weight_L2Basket_ampa": 0.0,
        "input_dist_A_weight_L2Basket_nmda": 0.0,
        "input_dist_A_weight_L2Pyr_ampa": 0.0,
        "input_dist_A_weight_L2Pyr_nmda": 0.0,
        "input_dist_A_weight_L5Pyr_ampa": 0.0,
        "input_dist_A_weight_L5Pyr_nmda": 0.0,
        "input_prox_A_delay_L2": 0.1,
        "input_prox_A_delay_L5": 1.0,
        "input_prox_A_weight_L2Basket_ampa": 0.0,
        "input_prox_A_weight_L2Basket_nmda": 0.0,
        "input_prox_A_weight_L2Pyr_ampa": 0.0,
        "input_prox_A_weight_L2Pyr_nmda": 0.0,
        "input_prox_A_weight_L5Basket_ampa": 0.0,
        "input_prox_A_weight_L5Basket_nmda": 0.0,
        "input_prox_A_weight_L5Pyr_ampa": 0.0,
        "input_prox_A_weight_L5Pyr_nmda": 0.0,
        "numspikes_evdist_1": 1,
        "numspikes_evprox_1": 1,
        "numspikes_evprox_2": 1,
        "prng_seedcore_evdist_1": 2,
        "prng_seedcore_evprox_1": 2,
        "prng_seedcore_evprox_2": 2,
        "prng_seedcore_extgauss": 2,
        "prng_seedcore_extpois": 2,
        "prng_seedcore_input_dist": 2,
        "prng_seedcore_input_prox": 2,
        "repeats_dist": 10,
        "repeats_prox": 10,
        "save_dpl": 0,
        "save_figs": 0,
        "save_spec_data": 0,
        "sigma_t_evdist_1": 3.85,
        "sigma_t_evprox_1": 2.47,
        "sigma_t_evprox_2": 8.33,
        "sim_prefix": "default",
        "sync_evinput": false,
        "t0_input_dist": 1000,
        "t0_input_prox": 1000.0,
        "t0_input_stdev_dist": 0.0,
        "t0_input_stdev_prox": 0.0,
        "t0_pois": 0.0,
        "t_evdist_1": 63.53,
        "t_evprox_1": 26.61,
        "t_evprox_2": 137.12,
        "threshold": 0.0,
        "tstop": 170,
        "tstop_input_dist": 1001,
        "tstop_input_prox": 1001
    }




Now, we update a few parameters


.. code-block:: default

    params.update({
        'dipole_scalefctr': 150000.0,
        'dipole_smooth_win': 0,
        'tstop': 310.0,
        't0_input_prox': 2000.0,
        'tstop_input_prox': 310.0,
        't0_input_dist': 50.0,
        'tstop_input_dist': 1001.0,
        't_evprox_1': 1000,
        'sigma_t_evprox_1': 2.5,
        't_evprox_2': 2000.0,
        'sigma_t_evprox_2': 7.0,
        't_evdist_1': 2000.0,
        'sigma_t_evdist_1': 6.0,
        'input_dist_A_weight_L2Pyr_ampa': 5.4e-5,
        'input_dist_A_weight_L5Pyr_ampa': 5.4e-5,
        'sync_evinput': 1,
        "prng_seedcore_input_dist": 3
    })








And we update all the conductances gbar related to the inputs
by using the pattern gbar_ev*


.. code-block:: default

    params['gbar_ev*'] = 0.0








Now let's simulate the dipole and plot it


.. code-block:: default

    net = Network(params)
    dpl = simulate_dipole(net)
    dpl[0].plot()




.. image:: /auto_examples/images/sphx_glr_plot_simulate_alpha_001.png
    :alt: agg
    :class: sphx-glr-single-img


.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none

    joblib will run over 1 jobs
    Building the NEURON model
    [Done]
    running trial 1 on 1 cores
    Simulation time: 0.03 ms...
    Simulation time: 10.0 ms...
    Simulation time: 20.0 ms...
    Simulation time: 30.0 ms...
    Simulation time: 40.0 ms...
    Simulation time: 50.0 ms...
    Simulation time: 60.0 ms...
    Simulation time: 70.0 ms...
    Simulation time: 80.0 ms...
    Simulation time: 90.0 ms...
    Simulation time: 100.0 ms...
    Simulation time: 110.0 ms...
    Simulation time: 120.0 ms...
    Simulation time: 130.0 ms...
    Simulation time: 140.0 ms...
    Simulation time: 150.0 ms...
    Simulation time: 160.0 ms...
    Simulation time: 170.0 ms...
    Simulation time: 180.0 ms...
    Simulation time: 190.0 ms...
    Simulation time: 200.0 ms...
    Simulation time: 210.0 ms...
    Simulation time: 220.0 ms...
    Simulation time: 230.0 ms...
    Simulation time: 240.0 ms...
    Simulation time: 250.0 ms...
    Simulation time: 260.0 ms...
    Simulation time: 270.0 ms...
    Simulation time: 280.0 ms...
    Simulation time: 290.0 ms...
    Simulation time: 300.0 ms...

    <Figure size 640x480 with 1 Axes>



We can confirm that what we simulate is indeed 10 Hz activity.


.. code-block:: default

    import matplotlib.pyplot as plt
    from scipy.signal import spectrogram
    import numpy as np
    sfreq = 1000. / params['dt']
    n_fft = 1024 * 8
    freqs, _, psds = spectrogram(
        dpl[0].data['agg'], sfreq, window='hamming', nfft=n_fft,
        nperseg=n_fft, noverlap=0)
    plt.figure()
    plt.plot(freqs, np.mean(psds, axis=-1))
    plt.xlim((0, 40))
    plt.xlabel('Frequency (Hz)')
    plt.ylabel('PSD')
    plt.show()



.. image:: /auto_examples/images/sphx_glr_plot_simulate_alpha_002.png
    :alt: plot simulate alpha
    :class: sphx-glr-single-img






.. rst-class:: sphx-glr-timing

   **Total running time of the script:** ( 1 minutes  34.621 seconds)


.. _sphx_glr_download_auto_examples_plot_simulate_alpha.py:


.. only :: html

 .. container:: sphx-glr-footer
    :class: sphx-glr-footer-example


  .. container:: binder-badge

    .. image:: images/binder_badge_logo.svg
      :target: https://mybinder.org/v2/gh/jonescompneurolab/hnn-core/gh-pages?filepath=stable/notebooks/auto_examples/plot_simulate_alpha.ipynb
      :alt: Launch binder
      :width: 150 px


  .. container:: sphx-glr-download sphx-glr-download-python

     :download:`Download Python source code: plot_simulate_alpha.py <plot_simulate_alpha.py>`



  .. container:: sphx-glr-download sphx-glr-download-jupyter

     :download:`Download Jupyter notebook: plot_simulate_alpha.ipynb <plot_simulate_alpha.ipynb>`


.. only:: html

 .. rst-class:: sphx-glr-signature

    `Gallery generated by Sphinx-Gallery <https://sphinx-gallery.github.io>`_
